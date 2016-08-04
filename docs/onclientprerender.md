This event is triggered every time before GTA renders a new frame.

Parameters
----------

``` lua
float timeSlice
```

-   **timeSlice:** The interval between this frame and the previous one in milliseconds (delta time).

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the client's [root element](/root_element.md "wikilink").

Example
-------

This example makes the camera follow the player in a GTA2-like way.

``` lua
root = getRootElement ()
function updateCamera ()
    local x, y, z = getElementPosition ( getLocalPlayer () )
    setCameraMatrix ( x, y, z + 50, x, y, z )
end
addEventHandler ( "onClientPreRender", root, updateCamera )
```

Warning
-------

This event and [onClientRender](/docs/onClientRender.md "wikilink") will trigger whatever function it is attached to with every frame. Depending on the server's maximum FPS and what your computer might handle - you might end up triggering the function 30-60 times **per second**.

As a result, this event may cause severe lag and/or even crashes if not used cautiously.

See Also
--------

### [Game Processing Order](/docs/Game_Processing_Order.md "wikilink")

### Other client events

### Client event functions
