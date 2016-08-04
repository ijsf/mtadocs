**Scripting the GUI - Tutorial 2 (Gates + Keypads)**

In this tutorial we will look at creating GUI keypads with combination codes for map-defined object gates. We will be using serverside keycodes, with some client - server interaction to verify the codes and report the outcome.

**Note that this tutorial assumes you are familiar with all the content covered in the [GUI Scripting Introduction](/docs/introduction_to_scripting_gui.md "wikilink").**

[thumb|GUI Keypad](/docs/image-gui_keypad_tutorial.png.md "wikilink")

Setting up the Keypad
---------------------

To begin, open up a clientside lua file (if you have been following the [GUI Scripting Introduction](/docs/introduction_to_scripting_gui.md "wikilink"), this is gui.lua) to work with.

### Creating the GUI

By now, GUI creation should seem relatively straight forward, so we will not go over this in too much detail. As in [Tutorial 1](/docs/scripting_the_gui_-_tutorial_1.md "wikilink") we will be using **absolute** values in this tutorial.

``` lua
function createKeypad()
    -- get the screen width and height
    local sWidth, sHeight = guiGetScreenSize()

    -- create the window, using some maths to find the centre of the screen
    local Width,Height = 142,276
    local X = (sWidth/2) - (Width/2)
    local Y = (sHeight/2) - (Height/2)
    keypadWindow = guiCreateWindow(X,Y,Width,Height,"Keypad",false)
    
    -- don't allow people to resize the keypad
    guiWindowSetSizable(keypadWindow,false)

    -- create buttons labeled 0-9, "*", "#", "Enter" and "C" (clear)
    keypadButton1 = guiCreateButton(13,68,37,36,"1",false,keypadWindow)
    keypadButton2 = guiCreateButton(53,68,37,36,"2",false,keypadWindow)
    keypadButton3 = guiCreateButton(93,68,37,36,"3",false,keypadWindow)
    keypadButton4 = guiCreateButton(13,108,37,36,"4",false,keypadWindow)
    keypadButton5 = guiCreateButton(53,108,37,36,"5",false,keypadWindow)
    keypadButton6 = guiCreateButton(93,108,37,36,"6",false,keypadWindow)
    keypadButton7 = guiCreateButton(13,148,37,36,"7",false,keypadWindow)
    keypadButton8 = guiCreateButton(53,148,37,36,"8",false,keypadWindow)
    keypadButton9 = guiCreateButton(93,148,37,36,"9",false,keypadWindow)
    keypadButtonAsterix = guiCreateButton(13,188,37,36,"*",false,keypadWindow)
    keypadButton0 = guiCreateButton(53,188,37,36,"0",false,keypadWindow)
    keypadButtonHash = guiCreateButton(93,188,37,36,"#",false,keypadWindow)
    keypadButtonExit = guiCreateButton(13,228,37,36,"Exit",false,keypadWindow)
    keypadButtonEnter = guiCreateButton(53,228,37,36,"Enter",false,keypadWindow)
    keypadButtonClear = guiCreateButton(93,228,37,36,"Clear",false,keypadWindow)

    -- create a gridlist to act as a backdrop on the kaypad display
    keypadGridlistDisplay = guiCreateGridList(13,25,117,33,false,keypadWindow)
    guiGridListSetSelectionMode(keypadGridlistDisplay,2)
    guiSetAlpha(keypadGridlistDisplay,0.6)
    -- create a label so we can write text on the keypad display
    keypadLabelDisplay = guiCreateLabel(14,26,115,30,"Enter Keycode.",false,keypadWindow)
    guiLabelSetColor(keypadLabelDisplay,255,000,000)
    guiLabelSetVerticalAlign(keypadLabelDisplay,"center")
    guiLabelSetHorizontalAlign(keypadLabelDisplay,"center",false)
    
    guiSetVisible(keypadWindow,false)
end

-- create the GUI when the resource starts
addEventHandler("onClientResourceStart",getResourceRootElement(getThisResource()),createKeypad)
```

As you can see, the keypad consists of 10 numerical keys (0-9), two character keys (\* and \#), a clear key, an exit key and an enter key. This means the codes used on the keypad can contain any of these characters (0123456789\*\#).

### Managing the display

We will begin by writing a small function to control the display on the keypad. This is done by encapsulating several methods of changing the text into a single function, which will enable us to easily add/remove text from the display later on.

``` lua
function updateDisplay(text)
    -- if we are passing some text
    if text then
        -- if its a digit or * or #, then append it to the end of the display
        if tonumber(text) or text == "*" or text == "#" then
            guiSetText(keypadLabelDisplay,guiGetText(keypadLabelDisplay) .. text)
        -- otherwise replace the display with the new text
        else
            guiSetText(keypadLabelDisplay,text)
        end 
    -- if we pass nil, clear the display entirely
    else
        guiSetText(keypadLabelDisplay,"")
    end
end
```

We can now simply call updateDisplay(our text) to change the text on the display, or updateDisplay(nil) to clear it.

### Detecting the clicks

With so many buttons that do very similar tasks on our keypad, there are two methods available to us for detecting when a player clicks on them.

We could add [onClientGUIClick](/docs/onclientguiclick.md "wikilink") events for every button individually, as we have done in previous tutorials; Or, alternatively, we could add a single [onClientGUIClick](/docs/onclientguiclick.md "wikilink") handle for the window (which is the parent of all our other keypad GUI elements), filter our results to include only the buttons we want and trigger our own custom event.

For the purposes of this tutorial and in the interest of outlining multiple approaches, we will explore the second method, though either one is an acceptable solution.

``` lua
addEventHandler("onClientGUIClick",keypadWindow,processKeypadClicks,true)
```

**Notice the final argument is set to 'true'. This means that clicks on any other elements in the same branch of the tree will also trigger this event handle (eg. clicks on our buttons).**

Add this line of code into your createKeypad function, after your GUI has been created.

Now that we are detecting all clicks on our GUI, we need to filter out the ones we do not want (ie: clicks on the window or display) and trigger our custom event:

``` lua
function processKeypadClicks(button,state)
    if button == "left" and state == "up" then
        -- if the source of this event is a gui button
        if getElementType(source) == "gui-button" then
            -- trigger our custom event and send the keypad id of this keypad as an argument
            triggerEvent("onKeypadButtonClicked",source,getElementData(keypadWindow,"keypadID"))
        end
    end
end
```

As you can see, we are now triggering our custom event “onKeypadButtonClicked” whenever a button is clicked on the keypad. Also note we use element data “keypadID” to differentiate between keypads. This data will need to be set whenever the player is shown a new keypad. We will cover this in more detail later.

### Handling the clicks

Much like when using [triggerServerEvent](/docs/triggerserverevent.md "wikilink") in previous tutorials, we now need to define the event, only this time it is purely clientside:

``` lua
addEvent("onKeypadButtonClicked",false)
addEventHandler("onKeypadButtonClicked",root,
    function(keypadID)

    end
)
```

Note the second argument in [addEvent](/docs/addevent.md "wikilink") is set to false, indicating that this event cannot be triggered from the server. Also note, the function we are using in the [addEventHandler](/docs/addeventhandler.md "wikilink") does not have a name. If you contract it down and remove the spacing, you get:

``` lua
addEventHandler("onKeypadButtonClicked",root,function() ... end)
```

This simply means instead of storing the pointer to the function in a variable, we are passing it directly as an argument. Doing it this way cleans up the code and will often make it easier to follow.

Now that the event has been created, we can fill in the code logic that will control our button presses.

``` lua
addEvent("onKeypadButtonClicked",false)
addEventHandler("onKeypadButtonClicked",root,
    function(keypadID)
        -- clear the display if this is the first time its being used
        if guiGetText(keypadLabelDisplay) == "Enter Keycode." or guiGetText(keypadLabelDisplay) == "Invalid Keycode." then
            updateDisplay()
        end
    
    
        -- if its the clear button
        if guiGetText(source) == "Clear" then
            -- clear the display
            updateDisplay()
        
        -- if its the enter button
        elseif guiGetText(source) == "Enter" then
            -- get the currently entered code from the display
            local code = guiGetText(keypadLabelDisplay)
            
            -- if they have entered a code
            if code then
                -- trigger the server so we can verify their code
                triggerServerEvent("verifyKeypadCode",getLocalPlayer(),code,keypadID)
            end
        
        -- if its the exit button
        elseif guiGetText(source) == "Exit" then
            -- hide the keypad and reset the display text ready for next time
            guiSetVisible(keypadWindow,false)
            updateDisplay("Enter Keycode.")
            showCursor(false,false)
            
        -- otherwise, it must be a character button
        else
            updateDisplay(guiGetText(source))   
        end
    end
)
```

Note how when we are clearing the display, we simply call updateDisplay() with no arguments. We do not need to pass 'nil' to it as all parameters (and variables) are nil by default.

Serverside Verification
-----------------------

For this part of the tutorial, you will need to open up a serverside lua file from your resource to work with.

### Defining the keycode

Now that we have completed the keypad clicking logic, we need to move on to verifying the code entered into the keypad. To do this, we need to have the correct code stored somewhere on the server, which we can check the players code against.

**Do not store sensitive information, such as keycodes or passwords, in a clientside file. All clientside files will be downloaded to the clients computer and can be accessed and read by anyone who has joined your server.**

For the purposes of this tutorial we will simply store the code in a serverside table, however it can be done any number of ways (such as serverside xml files or MySQL databases).

``` lua
local keypadCodes = {
    ["a51MainGateKeypadCode"] = "4455*#"
}
```

This table stores an entry called “a51MainGateKeypadCode” with the code 4455\*\#

**This is the keycode that you will use to open the gate later on in this tutorial.**

### Verifying the code

Now that we have a keycode to verify against, we can write our serverside event:

``` lua
addEvent("verifyKeypadCode",true)
addEventHandler("verifyKeypadCode",root,function(code,keypadID)
    if code then
        -- using the table we created earlier, check if the code supplied is the same as the code for this gate
        if code == keypadCodes[keypadID] then
            -- if it is, tell the client that it was successful
            triggerClientEvent(client,"onKeypadVerificationSuccessful",client,keypadID)
        else
            -- if it is not, tell the client that it was not successful
            triggerClientEvent(client,"onKeypadVerificationFailed",client,keypadID)
        end
    end
end)
```

Here we use our table and the keypadID supplied by the player to check if the codes match.

If you are not using a table to store the codes, then you will need to replace 'keypadCodes\[keypadID\]' with your own storage method. Once it is verified (or not), we can trigger the client so the appropriate information can be shown on the keypad display.

Receiving the result
--------------------

We have now finished the serverside section of the tutorial, so you will need to open up the clientside lua file from your resource that you were previously working on.

Once our code has been verified, the server will send back the response to the client. In just the same way as client -&gt; server interaction, we now need to add the event that the server is going to trigger on the client.

### Catching and processing the result

First we will add the event for when the verification is successful:

``` lua
addEvent("onKeypadVerificationSuccessful",true)
addEventHandler("onKeypadVerificationSuccessful",root,
    function()
        -- hide the keypad and reset the display text ready for next time
        guiSetVisible(keypadWindow,false)
        updateDisplay("Enter Keycode.")
        showCursor(false,false)
    end
)
```

Finally we can add the event for when the verification is unsuccessful:

``` lua
addEvent("onKeypadVerificationFailed",true)
addEventHandler("onKeypadVerificationFailed",root,
    function()
        -- update the display text to show the code was invalid
        updateDisplay("Invalid Keycode.")
    end
)
```

This completes the keypad section of the tutorial.

For an example of how to implement this into a working gate system, carry on reading the next section.

Applying the Keypad
-------------------

For the keypad to have any use, we need something to use it on. For this tutorial we will be using gates, and as mentioned earlier we will create a main gate into A51.

### Creating the gate

First of all, we need to create the gate object. For the purposes of this example, we will be using a map file to store the object. While this is the recommended method for defining objects, it is not the only way to approach it.

Navigate to your resource folder and make a new file called gate.map, then add your new map file to your meta.xml using:

``` lua
<map src="gate.map"/>
```

*If you are unsure of map file syntax, please see the [Writing Gamemodes Tutorial](/docs/writing_gamemodes.md "wikilink") or check the [Object](/docs/object.md "wikilink") page for help.*

``` lua
<map>
    <object id="a51MainGateKeypadCode" model="971" posX="96.736" posY="1918.352" posZ="20.694" rotX="0" rotY="0" rotZ="270.40" newPosX="96.751" newPosY="1914.474" newPosZ="20.694" />
</map>
```

This will create a gate object across the A51 entrance. The object will have position and rotation data, as well as its newPosX,newPosY and newPosZ information that we need to be able to move it.

**Note that the object id is the same as the table entry we created earlier to hold the access code.** This is one possible method that could be accessed to link this gate with that particular keycode.

### Opening the keypad

Back in the clientside lua file again, we can now work on linking the gate and the keypad.

Now that we have our gate, we need a way of accessing the keypad to open it. For the purposes of this tutorial we will use a simple command, however you could just as easily use a colshape or button press.

``` lua
addCommandHandler("a51gate",function()
    guiSetVisible(keypadWindow,true)
    showCursor(true,true)
    setElementData(keypadWindow,"keypadID","a51MainGateKeypadCode")
end)
```

Note that we set the element data “keypadID”. This is very important because it allows us to keep track of which gate we are trying to open (in this case, the “a51MainGateKeypadCode” gate).

### Opening the gate

With our gate created and our keypad ready, all thats left now is to open the gate. Having created custom events earlier for successfully and unsuccessfully verifying the code, this now becomes very easy to do. All we do is add an event handler for our custom “success” event, and using the keypadID we defined earlier we can move the gate inside it:

``` lua
addEventHandler("onKeypadVerificationSuccessful",root,
    -- keypadID is sent back from the server
    function(keypadID)
        -- get the gate object (this is where the id="a51MainGateKeypadCode" tag in the map file becomes useful)
        local gate = getElementByID(keypadID)

        -- if we found the object
        if gate then
            -- get the new position (as we defined in the map file)
            local x = tonumber(getElementData(gate,"newPosX"))
            local y = tonumber(getElementData(gate,"newPosY"))
            local z = tonumber(getElementData(gate,"newPosZ"))

            -- move the gate
            moveObject(gate,1500,x,y,z)
            
            -- get the original position
            x = tonumber(getElementData(gate,"posX"))
            y = tonumber(getElementData(gate,"posY"))
            z = tonumber(getElementData(gate,"posZ"))   
            
            -- set a timer to close the gate in 5 seconds
            setTimer(moveObject,5000,1,gate,1500,x,y,z)
        end
    end
)
```

Note how by using the keypadID sent back from the server, we can use if statements and checks against the id to control any number of gates from the same function.

You should now have a working example of a GUI Keypad controlling an A51 Gate.

For further GUI tutorials, see [Tutorial 3 (Scrolling News Feed)](/docs/scripting_the_gui_-_tutorial_3.md "wikilink")

[Category:GUI\_Tutorials](/docs/category-gui_tutorials.md "wikilink")
