This function sets the maximum text length that can be typed into an edit box.

Syntax
------

``` lua
bool guiEditSetMaxLength ( element theElement, int length )
```

### Required Arguments

-   **theElement:** The edit box to be changed.
-   **length:** An integer indicating the maximum number of characters that can be typed into the box.

### Returns

Returns *true* if the max length was set successfully, *false* otherwise.

Example
-------

This example creates an edit box with a limit on text length, alongside an “Output!” button. When the button is clicked, it will output the message in the edit box into the Chat Box.

``` lua
-- create our button
button = guiCreateButton( 0.7, 0.1, 0.2, 0.1, "Output!", true )
-- create an edit box and define it as "editBox".
editBox = guiCreateEdit( 0.3, 0.1, 0.4, 0.1, "Type your message here!", true )
-- set a maximum text length of 128 characters
guiEditSetMaxLength ( editBox, 128 )

-- setup our function to output the message to the chatbox
function outputEditBox ()
        local text = guiGetText ( editBox )   -- get the text from the edit box
        outputChatBox ( text )                -- output that text
end
addEventHandler ( "onClientGUIClick", button, outputEditBox )
```

See Also
--------
