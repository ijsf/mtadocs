This event is triggered when an element is clicked on by the client. These events can only trigger when the client has its cursor enabled. It triggers for all three mousebuttons in both their up and down states.

Parameters
----------

``` lua
string mouseButton, string buttonState, player playerWhoClicked, float clickPosX, float clickPosY, float clickPosZ
```

-   **mouseButton**: A string representing the mousebutton that was clicked. This might be *left*, *middle* or *right*.
-   **buttonState**: A string representing what state the button clicked is in. This might be *up* or *down*.
-   **playerWhoClicked**: The player that clicked on the element
-   **clickPosX**: The X position in the world the player clicked at
-   **clickPosY**: The Y position in the world the player clicked at
-   **clickPosZ**: The Z position in the world the player clicked at

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [element](/docs/element.md "wikilink") that got clicked by the player.

Example
-------

This example prints type of the element you clicked to chatbox when you click it.

``` lua
function elementClicked( theButton, theState, thePlayer )
    if theButton == "left" and theState == "down" then -- if left mouse button was pressed down
        outputChatBox( "You clicked " .. getElementType( source ), thePlayer ) -- print the element type to players chatbox
    end
end
addEventHandler( "onElementClicked", getRootElement(), elementClicked ) -- add a handler function for the event
```
