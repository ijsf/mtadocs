This event happens when any gui-element clicked

Parameters
----------

``` lua
string button, string state, int absoluteX, int absoluteY
```

-   **button:** the name of the button which will be clicked , it can be *left*, *right*, *middle*
-   **state:** the state of the mouse button, will be *down* if the mouse button was pushed, or *up* if it was released. **Please note currently only the *up* state is supported.**
-   **absoluteX:** the X position of the mouse cursor, in pixels, measured from the left side of the screen.
-   **absoluteY:** the Y position of the mouse cursor, in pixels, measured from the top of the screen.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the GUI element that was clicked.

**Note:**If you attach a GUI element to this event, when you click it's parent it will trigger too!

Example
-------

This example creates an edit box alongside an “Output!” button. When the button is clicked with the left mouse button, it will output the message in the edit box into the chat box.

``` lua
-- When client's resource starts, create the GUI
function initGUI( )
    -- Create our button
    btnOutput = guiCreateButton( 0.7, 0.1, 0.2, 0.1, "Output!", true )

    -- And attach our button to the outputEditBox function
    addEventHandler ( "onClientGUIClick", btnOutput, outputEditBox, false )

    -- Create an edit box and define it as "editBox".
    editBox = guiCreateEdit( 0.3, 0.1, 0.4, 0.1, "Type your message here!", true )
    guiEditSetMaxLength ( editBox, 128 ) -- The max chatbox text length is 128, so force this
end
addEventHandler( "onClientResourceStart", getResourceRootElement( getThisResource( ) ), initGUI )

-- Setup our function to output the message to the chatbox
function outputEditBox ( button )
    if button == "left" then
        local text = guiGetText ( editBox )-- Get the text from the edit box
        outputChatBox ( text ) -- Output that text
    end
end
```

[pl:onClientGUIClick](/docs/pl-onclientguiclick.md "wikilink")

See Also
--------

### GUI events

### Client event functions
