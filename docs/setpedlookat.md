Makes a ped turn his head and look at a specific world position or element.

Syntax
------

``` lua
bool setPedLookAt ( ped thePed, float x, float y, float z [, int time = 3000 [, int blend = 1000 ], element target = nil ] )
```

### Required Arguments

-   **thePed:** the ped to change the lookat of.
-   **x:** the x coordinate of the world position to look at.
-   **y:** the y coordinate of the world position to look at.
-   **z:** the z coordinate of the world position to look at.

### Optional Arguments

-   **time:** the time, in milliseconds, during which the ped will look at the target. Once this time has elapsed, he will look ahead again like before the function was applied. A time of 0 will immediately stop any lookat. A negative time will make the ped look at the target indefinitely.
-   **blend:** the time, in milliseconds, during which the look will blend.
-   **target:** if this argument is specified, the position arguments will be ignored and the ped's gaze will follow the specified element instead. Can be a player, a vehicle, another ped etc.

Example
-------

This example makes the local player look at where the camera points at. If you want to sync this effect with other players you can use [triggerLatentServerEvent](/docs/triggerlatentserverevent.md "wikilink") and [triggerLatentClientEvent](/triggerLatentClientEvent.md "wikilink") functions.

``` lua
local sx, sy = guiGetScreenSize()

function updateLookAt()
    -- The world coordinates of the center of the screen always are the point where the camera really looks at, so get them.
    local tx, ty, tz = getWorldFromScreenPosition(sx / 2, sy / 2, 10)
    setPedLookAt(localPlayer, tx, ty, tz, -1, 0) -- Make the player look that coordinates
end
addEventHandler("onClientPreRender", root, updateLookAt)
```

Issues
------

See Also
--------
