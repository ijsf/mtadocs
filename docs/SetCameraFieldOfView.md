Syntax
------

``` lua
bool setCameraFieldOfView ( string cameraMode, float fieldOfView )
```

### Required Arguments

**Note:** after 100, some unexpected things may happen to the camera, particularly in vehicles, use carefully!

-   **cameraMode:** the camera mode to get the field of view of
    -   “player”: whilst walking/running
    -   “vehicle”: whilst in vehicle
    -   “vehicle\_max”: the max the field of view can go to when the vehicle is moving at a high speed (must be higher than “vehicle”)
-   **fieldOfView:** The field of view angle, 0 to 179.

### Returns

Returns *true* if the arguments are valid, *false* otherwise.

Example
-------

In this example, the field of view for 'player walking/running' is set to 20 when the player joins.

``` lua
function setCameraFOVOnResStart()
    setCameraFieldOfView("player",20)
end
addEventHandler("onClientResourceStart", resourceRoot, setCameraFOVOnResStart)
```

See Also
--------
