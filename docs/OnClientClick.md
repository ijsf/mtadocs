This event triggers whenever the user clicks his mouse. This is linked to the GTA world, as oppose to GUI for which [onClientGUIClick](/docs/onClientGUIClick.md "wikilink") is to be used. This event allows detection of click positions of the 3D world.

Parameters
----------

``` lua
string button, string state, int absoluteX, int absoluteY, float worldX, float worldY, float worldZ, element clickedWorld
```

-   **button**: This refers the button used to click on the mouse, can be *left*, *right*, or *middle*
-   **state**: This can be used to tell if the user released or pressed the mouse button, where *up* is passed if the button is released, and *down* is passed if the button is pushed
-   **absoluteX**: This refers to the 2D *x coordinate* the user clicked on his screen, and is an *absolute* position in pixels.
-   **absoluteY**: This refers to the 2D *y coordinate* the user clicked on his screen, and is an *absolute* position in pixels.
-   **worldX**: This represents the 3D *x coordinate* the player clicked on the screen, and is relative to the GTA world.
-   **worldY**: This represents the 3D *y coordinate* the player clicked on the screen, and is relative to the GTA world.
-   **worldZ**: This represents the 3D *z coordinate* the player clicked on the screen, and is relative to the GTA world.
-   **clickedWorld**: This represents any physical [entity](/docs/entity.md "wikilink") elements that were clicked. If the player clicked on no MTA element, it's set to false.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the client's [root element](/root_element.md "wikilink").

Example
-------

This example creates a label when an element is clicked, the label displays in the position of the element telling you what kind of element you have clicked. It hides after 5 seconds.

``` lua
local myLabel = guiCreateLabel  ( 0, 0, 1, 1, "", true )

function addLabelOnClick ( button, state, absoluteX, absoluteY, worldX, worldY, worldZ, clickedElement )
        --if an element was clicked on screen
        if ( clickedElement ) then
                --retreive the element type
                local elementType = getElementType ( clickedElement )
                --change the label text to that element type
                guiSetText ( myLabel, elementType )
                --and place it in the position of where the element is
                guiSetPosition ( myLabel, absoluteX, absoluteY, false )
                --hide the text by passing an empty string 5 seconds later
                setTimer ( guiSetText, 5000, 1, myLabel, "" )
        end
end
addEventHandler ( "onClientClick", getRootElement(), addLabelOnClick )
```

[pl:onClientClick](/docs/pl:onClientClick.md "wikilink")

See Also
--------

### GUI events

### Client event functions
