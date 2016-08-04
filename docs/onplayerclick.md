This event is triggered when a player clicks using the mouse cursor.

Parameters
----------

``` lua
string mouseButton, string buttonState, element clickedElement, float worldPosX, float worldPosY, float worldPosZ, float screenPosX, float screenPosY
```

-   **mouseButton**: A string representing the mousebutton that was pressed. Value can be *left*, *middle* or *right*.
-   **buttonState**: A string representing the button state. Value can be *up* or *down*.
-   **clickedElement**: The element the player clicked on. This value is *nil* if none.
-   **worldPosX**: The X position in the world the player clicked on
-   **worldPosY**: The Y position in the world the player clicked on
-   **worldPosZ**: The Z position in the world the player clicked on
-   **screenPosX**: The X position on the screen the player clicked on
-   **screenPosY**: The Y position on the screen the player clicked on

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/docs/player.md "wikilink") that clicked.

Example
-------

This example outputs the state of the button they just pressed.

``` lua
function outputClick(mouseButton,buttonState)
    outputChatBox("Your "..mouseButton.." mouse button is now "..buttonState,source,255,255,0) -- output the state of the button they just pressed.
end
addEventHandler("onPlayerClick",getRootElement(),outputClick) -- When a player clicks trigger the outputClick function
```
