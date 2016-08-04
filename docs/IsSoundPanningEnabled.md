Syntax
------

``` lua
bool isSoundPanningEnabled ( element theSound )
```

### Required Arguments

-   **theSound :** A valid [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink").

### Returns

Returns *true* if the sound is valid and it has panning enabled, *false* if it does not or is not valid.

Example
-------

This example plays a *xy.mp3* file in the root folder of the resource which contains it at the center of the map, and proves that by default a sound enables panning by outputting the result of this function to the chatbox right after creating it. Then it disables the panning of the sound.

``` lua
local function testPanning()
    -- Create the sound and output the panning property state
    local sound = playSound3D("xy.mp3", 0, 0, 0)
    outputChatBox("By default, the sound has its panning " .. (isSoundPanningEnabled(sound) and "enabled" or "disabled"))
    -- Disable the panning and ouput a fact
    setSoundPanningEnabled(sound, false)
    outputChatBox("The sound panning was disabled, so it won't annoy you when the camera it's in a side anymore!", 0, 255, 0)
end
addEventHandler("onClientResourceStart", resourceRoot, testPanning)
```

Requirements
------------

See Also
--------
