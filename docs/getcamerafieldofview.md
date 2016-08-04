Syntax
------

``` lua
float getCameraFieldOfView ( string cameraMode )
```

### Required Arguments

-   **cameraMode:** the camera mode to get the field of view of
    -   “player”: whilst walking/running
    -   “vehicle”: whilst in vehicle
    -   “vehicle\_max”: the max the field of view can go to when the vehicle is moving at a high speed (must be higher than “vehicle”)

### Returns

Returns one float - the field of view angle

Example
-------

In this example, the field of view is output to the chat whenever the /getfov command is written

``` lua
function getCamFOV()
    outputChatBox("The camera field of view for 'player walking/running' is: " .. getCameraFieldOfView("player"))
end
addCommandHandler("getfov", getCamFOV)
```

See Also
--------
