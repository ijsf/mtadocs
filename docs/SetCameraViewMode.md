This function allows you to set the camera's view mode if you are inside a [vehicle](/docs/vehicle.md "wikilink"). This indicates at what distance the camera will follow the player.

Syntax
------

``` lua
bool setCameraViewMode ( int viewMode )
```

### Required Arguments

-   **viewMode**: The view mode you wish to use

### Returns

Returns *true* if the view was set correctly, *false* otherwise.

Example
-------

This example sets the camera to bumper view when the local player enters any vehicle.

``` lua
addEventHandler("onClientPlayerVehicleEnter", localPlayer, function()
  setCameraViewMode(0)
end)
```

See Also
--------
