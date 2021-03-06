**Scripting the GUI - Tutorial 3 (Scrolling News Feed)**

In this tutorial we will explore how to create a simple scrolling news feed GUI, allowing you to quickly and easily show server updates and other server information to your players. We will store all news items in a clientside xml file and use some simple xml reading to load them into the game.

We will then animate the news item to scroll along the bottom of the screen, updating the news text once it has scrolled beyond the edge of the screen.

**Note that this tutorial assumes you are familiar with all the content covered in the [GUI Scripting Introduction](/docs/introduction_to_scripting_gui.md "wikilink").**

Setting up the News Feed
------------------------

To begin, open up a clientside lua file (if you have been following the [GUI Scripting Introduction](/docs/introduction_to_scripting_gui.md "wikilink"), this is gui.lua) to work with.

### Creating the GUI

As with the previous tutorial, you should be suitably familiar with GUI creation already so we will not go into too much detail here.

``` lua
function createNewsFeed()
    -- get the screen width and height
    local sWidth, sHeight = guiGetScreenSize()
 
    -- create the gridlist, using some maths to find the bottom-centre of the screen
    local Width,Height = 800,45
    local X = (sWidth/2) - (Width/2)
    local Y = sHeight - (Height/2)
    
    -- the gridlist will act as the background to our news reel
    newsGridlist = guiCreateGridList(X,Y,Width,Height,false)
    
    -- create the label in the same place, but as a child of the gridlist
    -- also make it half the height of the gridlist, as half of the gridlist is off the bottom of the screen
    newsLabel = guiCreateLabel(X,Y,Width,Height/2,"Test text",false,newsGridlist)
    
    -- call our function to read the news out of the xml file
    loadNews()
    
    -- load the first news item in the table
    updateNewsItem(1)
    
    -- define a global variable called 'currentItem' with the value 1
    currentItem = 1
end

addEventHandler("onClientResourceStart",resourceRoot,createNewsFeed)
```

Note that the label is created as a child of the gridlist. Not only is this good practice in general, but it means that we can freely move parts of the label beyond the edge of the gridlist without them showing, which is critical to the visual effect of this tutorial.

Also notice the use of the 'resourceRoot' variable. This is an MTA variable that holds the root element value of the resource you are using it in.

The 'currentItem' variable is what we will use to keep track of which news item we are currently showing

### Writing the News

Now that we have our GUI created, we need some news to fill it with. To do this, we will read our news items out of a clientside xml file.

So, navigate to your resource directory and create a new xml file called newsfeed.xml (don't forget to add it to your meta.xml with the appropriate client tag).

Inside this file enter the following information:

``` lua
<root>
    <news>This is an example news item.</news>
    <news>From the 'Scripting the GUI' tutorial.</news>
    <news>Showing scrolling news text.</news>
    <news>Written on a GUI news feed.</news>
</root>
```

As you can see, each news item is defined as a <news> node with the value being the news text you want to display. There is no limit on how many news items you can add.

### Collecting the News

Once we have written all our news items, we will need to collect them all and store them in a table on the client. We will do this when the resource starts, saving us from having to repeatedly access the xml for new news items.

First, we need to define a table to store the items in:

``` lua
local newsItems = {}
```

Add this line to the top of your script. Make sure it is not inside a function otherwise it will not exist outside of that function (as denoted by the prefix “local”). When defined in the main body of the script it will exist in all functions.

Next, we will need to load the xml file:

``` lua
function loadNews()
    -- load our "newsfeed.xml" file
    local newsfile = xmlLoadFile("newsfeed.xml")
    
    -- if it was successfully loaded
    if newsfile then
    
        -- always remember to unload files once you are finished
        xmlUnloadFile(newsfile)
    end
end
```

**Always remember to unload files once you are finished using them.**

Finally, we can add some more code to our loadNews function to read the news items into our newsItems table:

``` lua
function loadNews()
    local newsfile = xmlLoadFile("newsfeed.xml")
    
    if newsfile then
        -- loop through all the children of the root node (the "news" nodes)
        for index,itemNode in ipairs(xmlNodeGetChildren(newsfile)) do
            -- get the text (the news item) from the node
            local item = xmlNodeGetValue(itemNode)
            
            -- insert it into our newsItems table
            table.insert(newsItems,item)
        end
    
        xmlUnloadFile(newsfile)
    end
end
```

We now have a table called 'newsItems' holding all of our news text from the xml file.

Updating the News
-----------------

Now that we have our GUI created and our news items ready, we need to write some code to update the news item being shown to players. As stated earlier, our news items will be shown on our 'newsLabel' GUI label.

To do this, we will write a simple function to get the next news item from our 'newsItems' table and display it in our label.

``` lua
-- define our function with a newIndex parameter, so that we can pass which news item we want to show
function updateNewsItem(newIndex)
    -- get the new news item from the table
    local item = newsItems[newIndex]
    
    -- update the label text
    guiSetText(newsLabel,item)
    
    -- update the 'currentItem' global variable
    currentItem = newIndex
end
```

### Sizing the Label

To make our news scrolling as accurate as possible, we need to be able to make the GUI label the same size as the news item text it is showing.

While this may seem like a tricky thing to do, it is made very easy with the function [guiLabelGetTextExtent](/docs/guilabelgettextextent.md "wikilink"). This will tell us the extent, or width, of the text currently shown in our label. So with a few modifications to our 'updateNewsItems' function, we get:

``` lua
function updateNewsItem(newIndex)
    local item = newsItems[newIndex]
    
    guiSetText(newsLabel,item)
    
    currentItem = newIndex
    
    -- get the current dimensions of the gui label
    local width,height = guiGetSize(newsLabel,false)
    
    -- get the text width of the label
    local extent = guiLabelGetTextExtent(newsLabel)
    
    -- update the size of the label with the new width (we do not change the height)
    guiSetSize(newsLabel,extent,height,false)
end
```

### Positioning the Label

Now that our GUI label is the correct width, we need to move it to a position where it is ready to scroll onto the screen.

Again, we can do this with a small modification to our 'updateNewsItems' function:

``` lua
function updateNewsItem(newIndex)
    local item = newsItems[newIndex]
    
    guiSetText(newsLabel,item)
    
    currentItem = newIndex
    
    local width,height = guiGetSize(newsLabel,false)
    
    local extent = guiLabelGetTextExtent(newsLabel)
    
    guiSetSize(newsLabel,extent,height,false)
    
    -- set the positon to the far right side of the gridlist, ready to scroll on to the left
    guiSetPosition(newsLabel,1,0,true)
end
```

Note the use of **relative** position values in the final line of the function.

In this case, it is far easier than calculating pixel values.

You can use both relative and absolute in the same script if you want to, the only limitation is that you cannot mix them in the same function call. The type of values you are using is defined by the final argument (true or false).

This means you cannot do the following and have it set to 400 pixels in, but 0.5% down

``` lua
guiSetPosition(yourElement,400,0.5,false)
```

The final argument “false” means both 400 and 0.5 will be read as pixel values.

Scrolling the News
------------------

The next step is to animate our news feed.

### Looking at Frames

To do this, we will introduce a new event: [onClientRender](/docs/onclientrender.md "wikilink"). As stated on the [onClientRender](/docs/onclientrender.md "wikilink") wiki page, this event is called every time GTA renders a new frame (ie: very often).

As usual, to use this event we will need to create an event handler for it:

``` lua
addEventHandler("onClientRender",root,scrollNews)
```

This will call our scrollNews function every frame, which we will then use to update the position of our news item.

**Make sure you add this handler after you have defined your scrollNews function.**

For our purposes, [onClientRender](/docs/onclientrender.md "wikilink") has one main advantage over, for example, [setTimer](/docs/settimer.md "wikilink"). As it is called every frame (and therefore is dependant on the players FPS), the movement of the news item will always appear to be completely smooth, unlike using a timer which would often appear to lag.

### Moving the News

In our 'updateNewsItem' function, we position the 'newsLabel' to the far right, so we will scroll in from the right to the left.

For this we will simply move the X position by -1 every frame:

``` lua
function scrollNews()
    -- if the newsLabel exists
    if newsLabel then
        -- get the current position of the label
        local x,y = guiGetPosition(newsLabel,false)
        
        -- set the new x position of the label as the old position -1
        guiSetPosition(newsLabel,x-1,y,false)
    end
end
```

### Looping around

Now that our news scrolls across the screen, we need to be able to check when it has scrolled too far to the left so we can start scrolling from the far-right side again.

We will also need to update the news item, so we should check the next item exists, and if it doesn't, go back to the first.

For this we will use some simple maths in a modification to our 'scrollNews' function:

``` lua
function scrollNews()
    local x,y = guiGetPosition(newsLabel,false)
    
    local labelWidth, labelHeight = guiGetSize(newsLabel,false)
    
    -- if the far right position of the label (x + labelWidth) is greater than or equal to 0 (ie: still showing on the gridlist)
    if ((x-1) + labelWidth) >= 0 then
        -- compensate for a small off-by-one bug in MTA
        if x <= 0 then x = x - 1 end
        
        -- update the position as normal
        guiSetPosition(newsLabel,x-1,y,false)
        
    -- otherwise, we move on to the next item and reset the position
    else
        -- get the total number of items in the 'newsItems' table
        local totalItems = #newsItems
        
        -- if the next item on our list does not exist in our table
        if (currentItem + 1) > totalItems then
            -- loop back to the first item in the list
            updateNewsItem(1)
        else
            -- otherwise move onto the next item in the list
            updateNewsItem(currentItem + 1)
        end
    end
end
```

Notice the use of the '\#' symbol to get the size of the 'newsItems' table. This is the Lua length operator, but it only works on tables that have numerical indexes (like an array or a list). It also works on strings, eg: \#“hello” would return 5.

That completes this section of the tutorial. For ideas on how to further improve and advance this code, continue reading the next section.

Improving the code
------------------

This section will detail several ways to improve upon the code you now have.

### GUI Customisation

To give your GUI a more unique feel, you have the ability to customise some aspects of your GUI elements.

For ideas on what is possible, browse the [MTA GUI functions](/docs/client_scripting_functions#gui_functions.md "wikilink").

For the purposes of this tutorial, we will be using Font, Colour and Alpha.

To start, we will change the alpha of the background gridlist GUI element we are using. To set the alpha, use [guiSetAlpha](/docs/guisetalpha.md "wikilink") and pass a value between 1 and 0; 1 being fully opaque and 0 being fully transparent.

``` lua
guiSetAlpha(newsGridlist,0.8)
```

Place this line of code in your 'createNewsFeed' function, after your gridlist has been created.

I find an alpha level of 0.8 looks best, however this is personal preference and you can experiment to suit your needs.

Next, we will look at the font of the label text. To set the font, use [guiSetFont](/docs/guisetfont.md "wikilink") and pass the string name of the font you want to use (available to see on the [Standard GUI Font Names](/docs/standard_gui_font_names.md "wikilink") page).

``` lua
guiSetFont(newsLabel,"default-bold-small")
```

Place this line of code in your 'createNewsFeed' function, after your label has been created.

Finally, we will look at setting the colour of the label text. To set the colour, use [guiLabelSetColor](/docs/guilabelsetcolor.md "wikilink") and pass the individual red,green and blue values.

``` lua
guiLabelSetColor(newsLabel,255,70,0)
```

Place this line of code in your 'createNewsFeed' function, after your label has been created.

This will give your news items an orange-red colour.

### Multiple News Items

In its current form, this code is only capable of showing one news item at a time. However, with a few modifications we can show multiple news items at once, one after another.

To begin with, we need to make sure we have a 'newItems' table defined at the very start of our script, as well as a 'distance' variable that will control the pixel distance between each news item:

``` lua
local newsItems = {}
local distance = 30
```

So put these lines at the top of the file.

Next, we will not know how many items we have (and consequently, how many labels we need) until we have loaded the file. With that in mind, we will move around some of the code in our 'createNewsFeed' function to support this:

``` lua
function createNewsFeed()
    -- get the screen width and height
    local sWidth, sHeight = guiGetScreenSize()
 
    -- create the gridlist, using some maths to find the bottom-centre of the screen
    local Width,Height = 800,45
    local X = (sWidth/2) - (Width/2)
    local Y = sHeight - (Height/2)
    
    -- the gridlist will act as the background to our news reel
    newsGridlist = guiCreateGridList(X,Y,Width,Height,false)
    
    guiSetAlpha(newsGridlist,0.8)
    
    -- call our function to read the news out of the xml file, before we create the labels
    loadNews()
        
    -- define a table to hold our labels
    newsLabel = {}
    
    -- now we can loop all our news items, and create a label for each one
    for index,item in ipairs(newsItems) do
    
        -- because we now have one label for every item, we can just set the text here and it wont need to be changed again.
        newsLabel[index] = guiCreateLabel(0,0,Width,Height/2,item,false,newsGridlist)
        
        guiSetFont(newsLabel[index],"default-bold-small")

        guiLabelSetColor(newsLabel[index],255,70,0)     

        -- modify the width of the label to fit the text
        local extent = guiLabelGetTextExtent(newsLabel[index])      
        guiSetSize(newsLabel[index],extent,Height/2,false)
        
        
        -- get the size of the gridlist
        local x,y = guiGetSize(newsGridlist,false)
        
        -- loop from 1 until index-1 in steps of 1
        -- this allows us to loop every label before the label we are currently on
        for i=1, index-1, 1 do
            -- tally up the sizes of all labels before our current one and store them in x
            local width = guiGetSize(newsLabel[i],false)
            x = x + width
        end
        
        -- put a 'distance' pixel gap between each news item
        x = x + (distance*(index-1))
        
        -- set the positon to the far right side of the gridlist, ready to scroll on to the left
        guiSetPosition(newsLabel[index],x,0,false)  
    end 
end
```

Now we need to update our 'updateNewsItem' function to account for having multiple labels:

``` lua
function updateNewsItem(newIndex)
    -- find the index of the news item directly infront (in the looping order) of the newIndex item
    local index = newIndex - 1
    if index == 0 then index = #newsItems end
    
    -- find the position of the right-edge of the label directly infront of the newIndex label
    local x = guiGetPosition(newsLabel[index],false) 
    local width = guiGetSize(newsLabel[index],false)
    x = x + width

    -- add a 'distance' pixel gap in
    x = x + distance

    -- check the new position isnt actually on the gridlist (ie: so it wont suddenly appear in the centre of the list)
    local gridlistWidth = guiGetSize(newsGridlist,false)
    
    if x < gridlistWidth then
        -- if it is, simple move it back to the edge
        x = gridlistWidth
    end
    
    -- set the new position
    guiSetPosition(newsLabel[newIndex],x,0,false)
end
```

Finally, we need to make some small adjustments to our 'scrollNews' function:

``` lua
function scrollNews()
    if newsItems then
        -- loop every news item
        for index,item in ipairs(newsItems) do
            local x,y = guiGetPosition(newsLabel[index],false)
            
            local labelWidth, labelHeight = guiGetSize(newsLabel[index],false)
            
            -- if the far right position of the label (x + labelWidth) is greater than or equal to 0 (ie: still showing on the gridlist)
            if ((x-1) + labelWidth) >= 0 then
                -- compensate for a small off-by-one bug in MTA
                if x <= 0 then x = x - 1 end
            
                -- update the position as normal
                guiSetPosition(newsLabel[index],x-1,y,false)
                
            -- otherwise, we move on to the next item and reset the position
            else
                updateNewsItem(index)
            end
        end
    end
end
```

You should now have multiple news items scrolling along your news feed simultaneously.

### Globally controlled scroll speed

As with the 'distance' variable above, we can set a global variable for controlling the scroll speed of the news items as well. Note that the speed will still be dependant on the players FPS (ie: lower FPS means slightly slower scrolling).

To do this, we simply need to create the variable at the start of our code:

``` lua
local scrollSpeed = 1
```

Put this line at the top of your file.

Then, we just replace the instance of “x-1” in our 'scrollNews' function with “x-scrollSpeed”:

``` lua
function scrollNews()
        ...
                -- update the position as normal
                guiSetPosition(newsLabel[index],x-scrollSpeed,y,false)
        ...
    end
end
```

That concludes this section of the tutorial.

[Category:GUI\_Tutorials](/docs/category-gui_tutorials.md "wikilink")
