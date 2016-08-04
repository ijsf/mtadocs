This event is triggered before GTA renders the HUD. This is particularly useful if you want to use [dxUpdateScreenSource](/docs/dxupdatescreensource.md "wikilink") to capture the screen onto a texture without capturing the HUD, or to alter HUD textures using [shaders](/docs/element/shader.md "wikilink") before they are drawn onto the screen.

Parameters
----------

*None*

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the client's [root element](/docs/root_element.md "wikilink").

Example
-------

``` lua
local render_count = 0

addEventHandler("onClientHUDRender", root, function()
    render_count = render_count + 1
end)

addEventHandler("onClientRender", root, function()
    render_count = render_count - 1
end)

addCommandHandler("getLossFrames", function()
    outputChatBox("Loss: "..render_count)
    outputDebugString("Loss: "..render_count, 3, 255, 0, 0)
end)
```

See Also
--------

### [Game Processing Order](/docs/game_processing_order.md "wikilink")

### Other client events

### Client event functions
