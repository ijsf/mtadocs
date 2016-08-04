In this tutorial we will make a simple rules window, with an accept button and a list of all the server rules & information.

**Note that this tutorial builds on content covered in the [GUI Scripting Introduction](/docs/Introduction_to_Scripting_the_GUI.md "wikilink").**

Making the GUI
--------------

### Getting set up

The first thing we need to do is create our GUI elements. For this tutorial we will be using one [window](/docs/Element/GUI/Window.md "wikilink"), one [button](/Element/GUI/Button.md "wikilink") and one [label](/Element/GUI/Text_label.md "wikilink"). We will be using **absolute** position values.

As noted in the [Previous tutorial](/docs/Introduction_to_Scripting_the_GUI.md "wikilink"), all the GUI must be made client side.

If you are following on from that tutorial, open up your gui.lua file to work with.

If you are not, browse to /Your MTA Server/mods/deathmatch/resources/myserver/ directory, and create a folder named “client”. Under /client/ directory, create a text file and name it “gui.lua”.

If you have not already done so, do not forget to include the new gui.lua file in the meta.xml of the main resource, and label it as a client script:

``` xml
<script src="client/gui.lua" type="client" />
```

### Making the window

In this file we will write a funtion that draws the window:

    -- create the function that will hold our gui creation code
    function createRulesWindow()
        -- get the screen width and height
        local sWidth, sHeight = guiGetScreenSize()
     
        -- create the window, using some maths to find the centre of the screen
        local Width,Height = 445,445
        local X = (sWidth/2) - (Width/2)
        local Y = (sHeight/2) - (Height/2)

        -- create the window
        rulesWindow = guiCreateWindow(X,Y,Width,Height,"Rules",false)
        
        -- stop players from being able to simply move the window out of the way
        guiWindowSetMovable(rulesWindow,false)
        
        -- stop players from being able to resize the window
        guiWindowSetSizable(rulesWindow,false)
    end

This will create a basic window in the centre of the screen that cannot be moved and cannot be resized.

### Making the button

Next, we will add the button to the bottom of our window that players can click on to accept the rules:

**Note that we are now writing more code for our existing 'createRulesWindow' function. This is not a new function and is meant to replace what you already have.**

    function createRulesWindow()
        -- get the screen width and height
        local sWidth, sHeight = guiGetScreenSize()
     
        -- create the window, using some maths to find the centre of the screen
        local Width,Height = 445,445
        local X = (sWidth/2) - (Width/2)
        local Y = (sHeight/2) - (Height/2)

        -- create the window and save the window gui element in a variable called 'rulesWindow'
        rulesWindow = guiCreateWindow(X,Y,Width,Height,"Rules",false)
        
        -- stop players from being able to simply move the window out of the way
        -- note that we use our 'rulesWindow' variable to make changes to the window
        guiWindowSetMovable(rulesWindow,false)
        
        -- stop players from being able to resize the window
        guiWindowSetSizable(rulesWindow,false)
        
        -- create the button and save the button gui element in a variable called 'rulesButton'
        rulesButton = guiCreateButton(137,394,158,37,"Accept",false,rulesWindow)
    end

### Making the label

Next, we will add the label to the centre of our window that our rules will be displayed on:

**Note that we are now writing more code for our existing 'createRulesWindow' function. This is not a new function and is meant to replace what you already have.**

    function createRulesWindow()
        -- get the screen width and height
        local sWidth, sHeight = guiGetScreenSize()
     
        -- create the window, using some maths to find the centre of the screen
        local Width,Height = 445,445
        local X = (sWidth/2) - (Width/2)
        local Y = (sHeight/2) - (Height/2)

        -- create the window and save the window gui element in a variable called 'rulesWindow'
        rulesWindow = guiCreateWindow(X,Y,Width,Height,"Rules",false)
        
        -- stop players from being able to simply move the window out of the way
        -- note that we use our 'rulesWindow' variable to make changes to the window
        guiWindowSetMovable(rulesWindow,false)
        
        -- stop players from being able to resize the window
        guiWindowSetSizable(rulesWindow,false)
        
        -- create the button and save the button gui element in a variable called 'rulesButton'
        rulesButton = guiCreateButton(137,394,158,37,"Accept",false,rulesWindow)
        
        -- create the label and save the label gui element in a variable called 'rulesLabel'
        -- we set the text of the label to our rules
        rulesLabel = guiCreateLabel(10,25,425,359,[[
        Welcome to my MTA Server!

        Please carefully read the rules before accepting.

        By accepting the rules, you are agreeing to play by them.
        Anyone caught breaking these rules will be kicked and/or banned from this server.

        If you do not accept the rules within 90 seconds, you will be kicked.

        1: No cheating.

        2: No bug abuse.

        3: No mods to your game.

        4: No flaming.

        5: Respect other players.

        6: Be nice!]],false,rulesWindow)
        
        -- set the horizontal alignment of the label to center (ie: in the middle of the window)
        -- also note the final argument "true" 
        -- this turns on wordwrap so if your text goes over the edge of the label, it will wrap around and start a new line automatically
        guiLabelSetHorizontalAlign(rulesLabel,"center",true)    
    end

*Note that the text is added in a different way to usual (we are not using quotation marks, "").*

### Text

There are *two* ways to define text for a label. For most situations, the recommended method is to enter all your text between quotation marks:

``` lua
guiSetText(guiElement,"My text here")
```

However, when we want to have more than 1 line in our text, it becomes just as easy to use the second method. It is purely dependant on situation and personal choice which method you chose. For clarity's sake, i will briefly outline both here.

When using quotation marks, we can make use of the newline character: "\\n" This allows us to break onto a new line in our text by entering "\\n". For example:

``` lua
guiSetText(guiElement,"This is line 1. \n This is line 2. \n This is line 3.")
```

However, if we use brackets to enclose the text instead of quotation marks, we do not need to worry about entering any extra characters. We can simply type the text out as we want it to appear in the label. For example:

``` lua
guiSetText(guiElement,[[This is line 1.
This is line 2.
This is line 3.]])
```

Both of these examples will create exactly the same text on the label. It is entirely up to you which method you chose to use.

### Using the function we wrote

The createRulesWindow function is now complete, but it won't do anything until we call it. It is recommended to create all GUI when the client resource starts, hide them, and show them to the player later when needed.

Therefore, we'll write an event handler for [onClientResourceStart](/docs/onClientResourceStart.md "wikilink") to create the window:

``` lua
-- attach the event handler to the root element of the resource
-- this means it will only trigger when its own resource is started
addEventHandler("onClientResourceStart", getResourceRootElement(getThisResource()), 
    function ()
        -- call the createRulesWindow function to create our gui
        createRulesWindow()
    end
)
```

As this is a rules window, we need to show the window when the player joins the game. Fortunately, GUI elements are visible by default so we do not need to write any more code to achieve this.

However, we will also need to show the cursor for the player. This can be done using the same event, [onClientResourceStart](/docs/onClientResourceStart.md "wikilink"), so we can modify the above code to include showing the cursor:

**Note that we are now writing more code for our 'onClientResourceStart' event. This is not a new function and is meant to replace what you already have.**

``` lua
-- attach the event handler to the root element of the resource
-- this means it will only trigger when its own resource is started
addEventHandler("onClientResourceStart", getResourceRootElement(getThisResource()), 
    function ()
        -- call the createRulesWindow function to create our gui
        createRulesWindow()
        
        -- show the cursor to the player
        showCursor(true,true)
    end
)
```

We now have a completed GUI rules window. Next, we need to write the button functionality for the accept button.

Scripting the Button
--------------------

Now that we have created our GUI, we need to make it work.

### Detecting the click

When the player clicks on any part of the GUI, the event "[onClientGUIClick](/docs/onClientGUIClick.md "wikilink")" will be triggered for the GUI component you clicked on. This allows us to easily detect any clicks on the GUI elements we want to use. For example, we can attach the event to the 'rulesButton' button to catch any clicks on it:

``` lua
-- attach the event onClientGUIClick to rulesButton and set it to trigger the 'acceptRules' function
addEventHandler("onClientGUIClick", rulesButton, acceptRules, false)
```

**Note the final argument passed is “false”. This indicates that the event will only trigger directly on rulesButton, not if the event has propagated up or down the tree. Setting this to “true” while attaching to gui elements will mean that clicking on any element in the same branch will trigger this event.**

This line of code can now be added inside the 'createRulesWindow' function. It is a common mistake to try and attach events to non-existant GUI elements, so make sure you always attach your events **after** the GUI element (in this case, the button) has been created:

``` lua
function createRulesWindow()
    -- create all our GUI elements
    ...

    -- now add our onClientGUIClick event to the button we just created
    addEventHandler("onClientGUIClick", rulesButton, acceptRules, false)
```

### Managing the click

Now that we can detect when the player clicks on the button, we need to write code to manage what happens when they do. In our [onClientGUIClick](/docs/onClientGUIClick.md "wikilink") event handle, we told it to call the function 'acceptRules' whenever 'rulesButton' is clicked. Therefore, we can now use the function 'acceptRules' to control what happens when the button is clicked:

``` lua
-- create the function and define the 'button' and 'state' parameters
-- (these are passed automatically by onClientGUIClick)
function acceptRules(button,state)
    -- if our accept button was clicked with the left mouse button, and the state of the mouse button is up
    if button == "left" and state == "up" then
        -- hide the window and all the components
        guiSetVisible(rulesWindow, false)
        
        -- hide the mouse cursor
        showCursor(false,false)
        
        -- output a message to the player
        outputChatBox("Thank you for accepting our rules. Have fun!")
        
        
        -- if the warning timer exists
        if rulesWarningTimer then
            -- stop the timer and set the variable to nil
            -- this is the timer used to kick players who do not accept the rules. We will cover this in more detail in the next section.
            killTimer(rulesWarningTimer)
            rulesWarningTimer = nil
        end
    end
end
```

Now, when the button is clicked, the window and the cursor will be hidden.

Checking for agreement
----------------------

Currently, our window will show when the player joins the server, and they must click accept to remove it. However, if they do not accept it they can stay in the server indefinately with the window open.

### Setting a timer

To combat this, we will add a timer using [setTimer](/docs/setTimer.md "wikilink") to kick them from the server after a period of time if they have not accepted the rules. First, we will need a global variable to store the timer pointer:

``` lua
local rulesWarningTimer = nil
```

Put this line at the very top of your script (it does not need to be inside a function)

Next, we will create our timer:

**Note that we are now writing more code for our existing 'createRulesWindow' function.**

``` lua
function createRulesWindow()
    -- create all of our gui
    ...
    
    -- set a timer for 30 seconds and set it to call our 'inactivePlayer' function with "1" as an argument
    rulesWarningTimer = setTimer(inactivePlayer,30000,1,1)
end
```

Put this [setTimer](/docs/setTimer.md "wikilink") line at the bottom of your 'createRulesWindow' function. This will create a timer that will trigger after 30 seconds.

### Giving a warning

Now we will write our 'inactivePlayer' function, to administer warnings to the player and finally kick him if he does not accept:

``` lua
-- create our function and define the 'status' parameter
-- the value of status will be passed from our setTimer function call
function inactivePlayer(status)
    -- if status is 1 (this means it is the first warning)
    if status == 1 then
        -- output a warning
        outputChatBox("Please accept our rules or be kicked.")
        
        -- set another timer to call inactivePlayer in another 30 seconds, with "2" as an argument
        rulesWarningTimer = setTimer(inactivePlayer,30000,1,2)
        
    -- if status is 2 (the second warning)
    elseif status == 2 then
        -- output a final warning
        outputChatBox("FINAL WARNING: Please accept our rules or be kicked.")
        
        -- set a final timer to call inactivePlayer in another 30 seconds, with "3" as an argument
        rulesWarningTimer = setTimer(inactivePlayer,30000,1,3)  
    elseif status == 3 then
        -- trigger the server so we can kick the player
        triggerServerEvent("clientKickInactivePlayer",getLocalPlayer())
    end
end
```

Note the use of [triggerServerEvent](/docs/triggerServerEvent.md "wikilink") to call the server. You should have experience with client-server interaction from the [Previous tutorial](/Introduction_to_Scripting_the_GUI.md "wikilink"). If not, you can go back and read the full explanation there.

We have now completed all the clientside code for this tutorial.

### Kicking the player

We now need to catch the event on the server that we triggered from the client, so open up a serverside lua file to work with.

To begin, we will add the event on the server:

``` lua
-- add the event, note the final argument "true" indicates it can be triggered from the client
addEvent("clientKickInactivePlayer",true)
-- add an event handler for this event to trigger the kickInactivePlayer function
addEventHandler("clientKickInactivePlayer",root,kickInactivePlayer)
```

**Make sure you add your event handler after you have defined your 'kickInactivePlayer' function.**

Note the use of [addEvent](/docs/addEvent.md "wikilink") and [addEventHandler](/addEventHandler.md "wikilink") on the server. You should have experience with client-server interaction from the [Previous tutorial](/Introduction_to_Scripting_the_GUI.md "wikilink"). If not, you can go back and read the full explanation there.

Finally, we will add the 'kickInactivePlayer' function to control kicking of the player:

``` lua
-- create our function
function kickInactivePlayer()
    -- kick the player
    kickPlayer(client,"Please accept our rules.")
end
```

Note the use of the 'client' variable, this is an MTA variable that holds the value of the client (player) that triggered the event.

**Note that [kickPlayer](/docs/kickPlayer.md "wikilink") will require your resource to have kick access in your ACL.**

**This is most easily accomplished by adding your resource into your admin group in the ACL:**

``` xml
<group name="Admin">
    ...
    <object name="resource.YourResourceName" />
    ...
</group>
```

For more information on the [ACL](/docs/ACL.md "wikilink"), see the [ACL](/ACL.md "wikilink") wiki page.

That concludes this tutorial. You should now have a fully working rules window for your server.

For further help with GUI, see the [GUI tutorials](/docs/:Category:GUI_Tutorials.md "wikilink").

[Category:GUI\_Tutorials](/docs/Category:GUI_Tutorials.md "wikilink")
