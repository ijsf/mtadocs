This function toggles the panning of a sound (hearing it closer to the left or right side of the speakers due to the camera position). By default a sound has its panning enabled.

Syntax
------

``` lua
bool setSoundPanningEnabled ( element sound, bool enable )
```

### Required arguments

-   **sound:** a [sound](/sound.md "wikilink") element to change the panning of.
-   **enable:** *true* to enable the panning, *false* otherwise.

### Returns

Returns *true* if the sound is valid and good arguments were passed, *false* if not.

If the sound is not 3D, this function will return *true* as well, but [isSoundPanningEnabled](/isSoundPanningEnabled.md "wikilink") will always return *true* after this (so it has no effect).

Example
-------

This example creates a sound at the center of the map when the resource which cointains it starts and adds a command called /soundpanning, which changes the panning of the sound.

``` lua
local panned = true
local sound = playSFX3D("script", 7, 1, 0, 0, 20, true)

function changePanning()
    if sound then
        setSoundPanningEnabled(sound, not panned)
        panned = not panned
        outputChatBox("Sound panning changed to " .. tostring(panned))
    else
        outputDebugString("Looks that your GTA was ripped.")
    end
end
addCommandHandler("soundpanning", changePanning)
```

See also
--------
