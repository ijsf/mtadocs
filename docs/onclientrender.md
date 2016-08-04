This event is triggered every time GTA renders a new frame. It is required for the DirectX drawing functions, and also useful for other clientside operations that have to be applied repeatedly with very short time differences between them.

Parameters
----------

*None*

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the client's [root element](/root_element.md "wikilink").

Example
-------

This example makes the camera follow the player in a GTA2-like way. This will be a little bit laggy. If you want the camera to follow something (eg. player or vehicle) then use [onClientPreRender](/docs/onClientPreRender.md "wikilink") instead.

``` lua
function updateCamera ()
    local x, y, z = getElementPosition ( localPlayer )
    setCameraMatrix ( x, y, z + 50, x, y, z )
end
addEventHandler ( "onClientRender", root, updateCamera )
```

Warning
-------

This event and [onClientPreRender](/docs/onClientPreRender.md "wikilink") will trigger whatever function it is attached to with every frame. Depending on the server's maximum FPS and what your computer might handle - you might end up triggering the function 30-60 times **per second**.

As a result, this event may cause severe lag and/or even crashes if not used cautiously.

See Also
--------

### [Game Processing Order](/docs/Game_Processing_Order.md "wikilink")

### Other client events

### Client event functions
