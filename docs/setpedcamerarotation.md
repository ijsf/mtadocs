This function sets the camera rotation of a ped, e.g. where its camera will look at. Don't confuse this with [getCameraMatrix](/docs/getCameraMatrix.md "wikilink"), because that function is designed for fixed (scripted) camera moves.

Syntax
------

``` lua
bool setPedCameraRotation ( ped thePed, float cameraRotation )
```

### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") whose camera rotation is to be changed.
-   **cameraRotation:** The new direction that the ped will walk if you set their forwards control state. If the ped is the local player, it will also change where his camera is looking at if it isn't fixed (i.e. camera target is the local player).

### Returns

Returns *true* if the camera rotation was changed, *false* otherwise.

Example
-------

The next code snippet adds a command called /rotatecam, which rotates the camera of the player who uses it.

``` lua
function rotateLocalPlayerCamera()
    --setPedCameraRotation(localPlayer, getPedCameraRotation(localPlayer) + 45) -- This would work if getPedCameraRotation returned non-transformed angles
    setPedCameraRotation(localPlayer, -(getPedCameraRotation(localPlayer) + 45)) -- Tranform the angle returned and then add 45º to it
    outputChatBox("Your camera was rotated 45 degrees counter clockwise.", 0, 255, 0)
end
addCommandHandler("rotatecam", rotateLocalPlayerCamera)
```

See Also
--------
