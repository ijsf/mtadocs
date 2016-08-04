**Scripting the Gui - Tutorial 1 (Gridlists)**

In this tutorial we will explore the use of gridlists in creating a vehicle selection screen, with optional clientside vehicle xml data reading.

**Note that this tutorial assumes you are familiar with all the content covered in the [Previous tutorial](/docs/introduction_to_scripting_gui.md "wikilink").**

Setting up the Vehicle Selection
--------------------------------

### Creating the GUI

To begin, open up a clientside lua file (if you have been following the [Scripting Introduction](/docs/scripting_introduction.md "wikilink"), this is gui.lua) to work with.

In this file, we will start writing our function for creating the GUI. As covered in the [Previous tutorial](/docs/introduction_to_scripting_gui.md "wikilink"), there are 2 value type options available when creating gui: **relative** and **absolute**.

For the purposes of this tutorial, we will be using **absolute** values.

This will create a simple GUI with a window, gridlist and button:

``` lua
function createVehicleSelection()
    -- get the screen width and height
    local sWidth, sHeight = guiGetScreenSize()
    
    -- use some simple maths to position the window in the centre of the screen
    local Width,Height = 376,259
    local X = (sWidth/2) - (Width/2)
    local Y = (sHeight/2) - (Height/2)
    windowVehicleSelection = guiCreateWindow(X,Y,Width,Height,"Vehicle Selection Window",false)
    
    gridlistVehicleSelection = guiCreateGridList(10,26,357,192,false,windowVehicleSelection)
    -- add a "Vehicle" and a "Type" collumn to the gridlist
    guiGridListAddColumn(gridlistVehicleSelection,"Vehicle",0.2)
    guiGridListAddColumn(gridlistVehicleSelection,"Type",0.2)
    
    -- set the default width of the columns to roughly half the size of the gridlist (each)
    guiGridListSetColumnWidth(gridlistVehicleSelection,1,0.4,true)
    guiGridListSetColumnWidth(gridlistVehicleSelection,2,0.5,true)
    
    buttonCreate = guiCreateButton(121,227,120,20,"Create",false,windowVehicleSelection)
    
    -- add the event handler for when the button is clicked
    addEventHandler("onClientGUIClick",buttonCreate,createVehicleHandler,false)
    
    -- hide the GUI
    guiSetVisible(windowVehicleSelection,false)
    
    -- this will add all the vehicle options onto the gridlist, it is explained later in this tutorial
    populateGridlist()
end
```

We now also need to call this function somewhere, otherwise the GUI will never be created. As in previous tutorials, to do this we can use [onClientResourceStart](/docs/onclientresourcestart.md "wikilink").

``` lua
-- when the resource is started, create the GUI and hide it
addEventHandler("onClientResourceStart",getResourceRootElement(getThisResource()),
    function()
        createVehicleSelection()
    end
)
```

### Showing the GUI

Unlike in previous tutorials, we want players to be able to open this window whenever they chose, not when the resource starts. So, we can add a [Command](/docs/addcommandhandler.md "wikilink") to do this.

``` lua
-- create the function that will show the window
function showVehicleSelection()
    -- if the window isnt visible, show it
    if not guiGetVisible(windowVehicleSelection) then
        guiSetVisible(windowVehicleSelection,true)
        
        showCursor(true,true)
    end
end

-- add the command /vehicleselection and set it to call the showVehicleSelection function
addCommandHandler("vehicleselection",showVehicleSelection)
```

### Populating the Gridlist from a table

Now that we have our basic GUI created, we need to fill the gridlist with all of our vehicles.

To begin with, we will do this using a simple clientside table. Later in the tutorial, we will explore expanding this method to use .xml files for storing information. To begin, we must create a small table containing a selection of vehicles that we can spawn.

The table contains vehicles in the format \[“description”\] = vehicle\_id :

``` lua
-- create the table and fill it with a selection of vehicle ids and names
local vehicleSelectionTable = {
    ["Sparrow"] = 469,
    ["Stuntplane"] = 513,
    ["BF-400"] = 581,
    ["Freeway"] = 463,
    ["Speeder"] = 452,
    ["Jester"] = 559,
    ["Sabre"] = 475,
    ["Police Ranger"] = 599,
    ["Utility Van"] = 552,
    ["Tug"] = 583
}
```

Place this code at the very top of your file (it does not need to be inside a function).

Next, we can write our “populateGridlist” function which will fill the Gridlist with all the vehicles in the table. To do this we simply need to loop through all the values in the table, adding each one to the gridlist as we go. We will also set hidden data using [guiGridListSetItemData](/docs/guigridlistsetitemdata.md "wikilink") to store the vehicle id:

``` lua
function populateGridlist()
    -- loop through the table
    for name,vehicle in pairs(vehicleSelectionTable) do
        -- add a new row to the gridlist
        local row = guiGridListAddRow(gridlistVehicleSelection)

        -- set the text in the first column to the vehicle name
        guiGridListSetItemText(gridlistVehicleSelection,row,1,name,false,false)
        -- set the text in the second column to the vehicle type
        guiGridListSetItemText(gridlistVehicleSelection,row,2,getVehicleType(vehicle),false,false)
        
        -- set the data for gridlist slot as the vehicle id
        guiGridListSetItemData(gridlistVehicleSelection,row,1,tostring(vehicle))
    end
end
```

### Managing the click

Now that we have our GUI completed, we need to be able to catch any clicks made on the “create” button. We have attached the [onClientGUIClick](/docs/onclientguiclick.md "wikilink") event to buttonCreate already, so now we need to write the function that it calls. In this function we do some basic error checking, such as making sure a vehicle has been selected in the list. We can then use some maths to find a position infront of the player and send the server this information to spawn the vehicle (using [triggerServerEvent](/docs/triggerserverevent.md "wikilink"))

``` lua
function createVehicleHandler(button,state)
    if button == "left" and state == "up" then
        -- get the selected item in the gridlist
        local row,col = guiGridListGetSelectedItem(gridlistVehicleSelection)
        
        -- if something is selected
        if row and col and row ~= -1 and col ~= -1 then
            -- get the vehicle id data from the gridlist that is selected
            local selected = guiGridListGetItemData(gridlistVehicleSelection,row,col)
            
            -- make sure the vehicle id is a number not a string
            selected = tonumber(selected)
                        
            -- get the players position and rotation
            local rotz = getPedRotation(getLocalPlayer())
            local x,y,z = getElementPosition(getLocalPlayer())
            -- find the position directly infront of the player
            x = x + ( math.cos ( math.rad ( rotz+90 ) ) * 3)
            y = y + ( math.sin ( math.rad ( rotz+90 ) ) * 3)
            
            if selected and x and y and z then
                -- trigger the server
                triggerServerEvent("createVehicleFromGUI",getRootElement(),selected,x,y,z)
                
                -- hide the gui and the cursor
                guiSetVisible(windowVehicleSelection,false)
                showCursor(false,false)
            else
                outputChatBox("Invalid arguments.")
            end
        else
            -- otherwise, output a message to the player
            outputChatBox("Please select a vehicle.")
        end
    end
end
```

### Creating the Vehicle

At this point we now have all the code needed on the client side, so open up a serverside .lua file to work with.

On the server side, we will first of all need to define the custom event that we triggered before from the client. This can be done using [addEvent](/docs/addevent.md "wikilink") and [addEventHandler](/docs/addeventhandler.md "wikilink"). Finally we will need a small function for creating the vehicle:

``` lua
function createMyVehicle(vehicleid,x,y,z)
    -- check all the arguments exist
    if vehicleid and x and y and z then
        createVehicle(vehicleid,x,y,z)
    end
end

addEvent("createVehicleFromGUI",true)
addEventHandler("createVehicleFromGUI",root,createMyVehicle)
```

Note the use of the “root” variable. This is an MTA variable containing the root element; every resource has one.

This completes the first section of the tutorial. You should now have a basic, working vehicle spawn script.

In the second section, we will cover collapsible gridlist data and clientside xml file reading.

Expanding the code
------------------

This section will detail several ways to improve upon the code you now have.

### Importing Data

One big improvement over the previously mentioned method is to use external files to store the vehicle information, allowing us to much more quickly and easily manage large amounts of data. For this tutorial, we will use a clientside xml file to hold the information.

First of all you will need to create your xml file, so navigate to your resources directory and create a new file named vehicles.xml:

*For the purpose of this example, we will include only a small fraction of the total vehicles, however the file can easily be expanded to include them all.*

If you are unsure of xml data structures, you can browse the [MTA xml functions](/docs/server_scripting_functions#xml_functions.md "wikilink") for help.

``` lua
<root>
    <group type="Bikes">
        <vehicle id="581" name="BF-400"/>
        <vehicle id="463" name="Freeway"/>
        <vehicle id="481" name="BMX"/>
    </group>
    <group type="Boats">
        <vehicle id="472" name="Coastguard"/>
        <vehicle id="452" name="Speeder"/>
    </group>
    <group type="Helicopters">
        <vehicle id="487" name="Maverick"/>
        <vehicle id="469" name="Sparrow"/>  
    </group>
    <group type="Planes">
        <vehicle id="593" name="Dodo"/>
        <vehicle id="513" name="Stuntplane"/>   
    </group>
    <group type="Sports Cars">
        <vehicle id="565" name="Flash"/>
        <vehicle id="559" name="Jester"/>
        <vehicle id="477" name="ZR-350"/>   
    </group>
    <group type="2-Door">
        <vehicle id="474" name="Hermes"/>
        <vehicle id="475" name="Sabre"/>
    </group>
    <group type="Emergency">
        <vehicle id="416" name="Ambulance"/>
        <vehicle id="599" name="Police ranger"/>
    </group>
    <group type="Industrial">
        <vehicle id="573" name="Dune"/>
        <vehicle id="552" name="Utility van"/>  
    </group>
    <group type="Misc">
        <vehicle id="457" name="Caddy"/>
        <vehicle id="583" name="Tug"/>
    </group>
</root>
```

Once you have created your file, do not forget to add it to the meta.xml of your resource with the appropriate client tag.

Note the group “type” tag. This is an arbitrary description of the vehicles contained within the group and can be renamed or added as any text. Similarly, the vehicle “name” tag is also just a textual description of the vehicle and does not need to be the exact vehicle name.

Now that we have the data, we can import it into the game and display it in the GUI. **If you are following on from the first section of this tutorial, this new code will replace what is inside your existing 'populateGridlist' function.** First, we need to load the file:

``` lua
function populateGridlist()
    -- load the file and save the root node value it returns
    local rootnode = xmlLoadFile("vehicles.xml")
    
    -- check that the file exists and has been correctly loaded
    if rootnode then        
        -- unload the xml file
        xmlUnloadFile(rootnode)
    end
end
```

Always make sure you unload any files once you are finished using them.

We can now start collecting the data from the file and entering it into our gridlist. We can do this by looping through the xml data (in a similar manner to looping through the vehicle table earlier in this tutorial) and adding each entry into the list.

``` lua
function populateGridlist()
    local rootnode = xmlLoadFile("vehicles.xml")
    
    if rootnode then        
        -- first, we find every "group" node (they are direct children of the root)
        for _,group in ipairs(xmlNodeGetChildren(rootnode)) do
            -- add a new row to the gridlist
            local row = guiGridListAddRow(gridlistVehicleSelection)

            -- get the group name
            local name = xmlNodeGetAttribute(group,"type")
            
            -- set the text in the first column to the group type and indicate it is a section ('true')
            -- (sections on gridlists show up in bold and cannot be clicked)
            guiGridListSetItemText(gridlistVehicleSelection,row,1,name,true,false)          
        
            -- then, for every group that we find, loop all of its children (the vehicle nodes)
            -- and add them into the gridlist
            for _,vehicle in ipairs(xmlNodeGetChildren(group)) do
                -- add a new row to the gridlist
                row = guiGridListAddRow(gridlistVehicleSelection)

                -- get the vehicle name and id
                name = xmlNodeGetAttribute(vehicle,"name")
                local id = xmlNodeGetAttribute(vehicle,"id")
                
                -- set the text in the first column to the vehicle name
                guiGridListSetItemText(gridlistVehicleSelection,row,1,name,false,false)
                -- set the text in the second column to the vehicle type
                guiGridListSetItemText(gridlistVehicleSelection,row,2,getVehicleType(tonumber(id)),false,false)     
                
                -- finally, set the vehicle id as data so we can access it later
                guiGridListSetItemData(gridlistVehicleSelection,row,1,tostring(id))
            end
        end 
    
        -- unload the xml file now that we are finished
        xmlUnloadFile(rootnode)
    end
end
```

Note the use of for loops in the code with [xmlNodeGetChildren](/docs/xmlnodegetchildren.md "wikilink"). This saves us a lot of time and effort as we do not have to manually code each group and vehicle into the list.

You should now have a fully working vehicle selection menu, reading all of its data from a clientside xml file. Next, we will examine how to generate the appearance of collapsing and expanding sections in a gridlist.

### Collapsing/Expanding the Gridlist

Allowing sections of the gridlist to be collapsed or expanded gives much more control over the visible content to the user. This frees up space on the screen and makes the whole menu much more comfortable to use.

### Loading the data

To be able to achieve this effect (as it is not a natural feature of gridlists) we will need to load the vehicle information into a table (from the xml file), rather than directly including it all in the gridlist. **If you are following on from a previous section of this tutorial, this new code will replace what is inside your existing 'populateGridlist' function.**

This works in much the same way the previous xml loading example does, only this time instead of saving the data into the gridlist, we save it into a table entry instead. We also set the custom data “header” on the gridlist slots to denote which gridlist entries are our “group” entries and which are vehicles.

``` lua
function populateGridlist()
    local rootnode = xmlLoadFile("vehicles.xml")
    
    -- create a blank global table to store our imported data
    vehicleTable = {}
    
    if rootnode then        
        for _,group in ipairs(xmlNodeGetChildren(rootnode)) do
            -- create an entry in the gridlist for every vehicle "group"
            local row = guiGridListAddRow(gridlistVehicleSelection)

            local name = xmlNodeGetAttribute(group,"type")
            
            guiGridListSetItemText(gridlistVehicleSelection,row,1,name,false,false) 

            -- add an entry containing the group name into the table
            vehicleTable[name] = {}
            
            -- we will use the custom data "header" to indicate that this entry can be expanded/collapsed
            guiGridListSetItemData(gridlistVehicleSelection,row,1,"header") 
        
            -- then, for every group that we find, loop all of its children (the vehicle nodes) and store them in a table
            for _,vehicle in ipairs(xmlNodeGetChildren(group)) do
                local vname = xmlNodeGetAttribute(vehicle,"name")
                local id = xmlNodeGetAttribute(vehicle,"id")            
            
                -- insert both the vehicle id and the vehicle description into the table
                table.insert(vehicleTable[name],{id,vname})
            end
        end 
    
        -- set element data on the gridlist so we know which group is currently showing
        setElementData(gridlistVehicleSelection,"expanded","none")
    
        -- unload the xml file now that we are finished
        xmlUnloadFile(rootnode)
    end
end
```

Now that we have all the data stored, we can quickly manipulate it when neccessary.

### Managing the double click

To enable the player to simply double click on a group name to expand/collapse it we need to use the [onClientGUIDoubleClick](/docs/onclientguidoubleclick.md "wikilink") event. If we attach it to the gridlist, we can then catch any double clicks on the group names in it:

``` lua
-- attach the onClientGUIDoubleClick event to the gridlist and set it to call processDoubleClick
addEventHandler("onClientGUIDoubleClick",gridlistVehicleSelection,processDoubleClick,false)
```

Add this line of code in your createVehicleSelection, after the gridlist has been created.

As the gridlist items are not separate GUI elements, we must capture all clicks from anywhere on the gridlist then process them to filter out the ones we do not want. This can be done by checking if an item is selected, then checking if the item is one of our “group” values (using our previously mentioned “header” data):

``` lua
function processDoubleClick(button,state)
    if button == "left" and state == "up" then
        local row,col = guiGridListGetSelectedItem(gridlistVehicleSelection)
        
        -- if something in the gridlist has been selected
        if row and col and row ~= -1 and col ~= -1 then     
            -- if it is a header
            if guiGridListGetItemData(gridlistVehicleSelection,row,col) == "header" then
                local selected = guiGridListGetItemText(gridlistVehicleSelection,row,col)
                
                -- call the function to collapse or expand the menu and pass which section it is as an argument
                changeGridlistState(selected)
            end
        end
    end
end
```

Once we have narrowed down the double clicks to only those done on our group headers, we can expand/collapse them appropriately. This can be done by simply setting new text values in the gridlist according to the newly expanded/collapsed group, which creates the convincing illusion of collapsable menus.

Note that much of the following code is reused from previous areas of this tutorial. While it is generally bad practice to clone sections of code in this way, for the purposes of this example it is far easier to understand.

``` lua
function changeGridlistState(group)
    if group then
        -- if the group is already expanded, we want to collapse it
        if getElementData(gridlistVehicleSelection,"expanded") == group then
            -- first, we clear all previous data from the gridlist
            guiGridListClear(gridlistVehicleSelection)
            
            -- now, loop all the group entries in the vehicle table that we created earlier
            for group,_ in pairs(vehicleTable) do
                -- add each group to the list and mark them with "header"           
                local row = guiGridListAddRow(gridlistVehicleSelection)
                
                guiGridListSetItemText(gridlistVehicleSelection,row,1,group,false,false)    
                guiGridListSetItemData(gridlistVehicleSelection,row,1,"header") 
            end
            
            -- update the data to indicate that no groups are currently expanded
            setElementData(gridlistVehicleSelection,"expanded","none")
            
        -- otherwise, we want to expand it
        else
            guiGridListClear(gridlistVehicleSelection)
            
            local row = guiGridListAddRow(gridlistVehicleSelection)
            
            guiGridListSetItemText(gridlistVehicleSelection,row,1,group,false,false)    
            guiGridListSetItemData(gridlistVehicleSelection,row,1,"header")             
            
            -- loop every vehicle in the specified groups table
            for _,vehicle in ipairs(vehicleTable[group]) do
                -- add them to the gridlist and set the vehicle id as data
                row = guiGridListAddRow(gridlistVehicleSelection)
            
                -- format a "-" into the string to make it visually easier to distinguish between groups and vehicles
                guiGridListSetItemText(gridlistVehicleSelection,row,1,"- "..vehicle[2],false,false) 
                guiGridListSetItemText(gridlistVehicleSelection,row,2,getVehicleType(tonumber(vehicle[1])),false,false) 
                                            
                guiGridListSetItemData(gridlistVehicleSelection,row,1,tostring(vehicle[1]))
            end 

            -- update the data to indicate which group is currently expanded
            setElementData(gridlistVehicleSelection,"expanded",group)           
        end
    end
end
```

This comletes the second section of the tutorial.

For further GUI tutorials, see [Tutorial 2 (Gates and Keypads)](/docs/scripting_the_gui_-_tutorial_2.md "wikilink")

[Category:GUI\_Tutorials](/docs/category:gui_tutorials.md "wikilink")
