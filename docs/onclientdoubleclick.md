This event triggers whenever the user double-clicks his mouse. This is linked to the GTA world, as appose to GUI for which [onClientGUIDoubleClick](/docs/onclientguidoubleclick.md "wikilink") is to be used. This event allows detection of click positions of the 3D world.

Parameters
----------

``` lua
string button, int absoluteX, int absoluteY, float worldX, float worldY, float worldZ, element clickedWorld
```

-   **button**: This refers the button used to click on the mouse, can be *left*, *right*, or ''middle'
-   **absoluteX**: This refers to the 2D *x coordinate* the user clicked on his screen, and is an *absolute* position in pixels.
-   **absoluteY**: This refers to the 2D *y coordinate* the user clicked on his screen, and is an *absolute* position in pixels.
-   **worldX**: This represents the 3D *x coordinate* the player clicked on the screen, and is relative to the GTA world.
-   **worldY**: This represents the 3D *y coordinate* the player clicked on the screen, and is relative to the GTA world.
-   **worldZ**: This represents the 3D *z coordinate* the player clicked on the screen, and is relative to the GTA world.
-   **clickedWorld**: This represents any physical [entity](/docs/entity.md "wikilink") elements that were clicked. If the player clicked on no MTA element, it's set to false.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the client's [root element](/docs/root_element.md "wikilink").

Example
-------

``` lua
function onMyMouseDoubleClick (button, absoluteX, absoluteY, worldX, worldY,  worldZ, clickedWorld)
    if button == "left" then 
        playSoundFrontEnd(40)
    end
end
addEventHandler("onClientDoubleClick", root, onMyMouseDoubleClick)
```

[pl:onClientDoubleClick](/docs/pl-onclientdoubleclick.md "wikilink")

See Also
--------

### GUI events

### Client event functions
