This function allows retrieval of where a ped's target is blocked. It will only be blocked if there is an obstacle within a ped's target range.

Syntax
------

``` lua
float float float getPedTargetCollision ( ped targetingPed )
```

### Required Arguments

-   **targetingPed:** This is the ped whose target collision you wish to retrieve

### Returns

Returns three floats, *x*,*y*,*z*, representing the position where the ped's target collides, or *false* if it was unsuccessful.

Example
-------

This Example draws a line from where the Ped´s Target Starts to the Point where the Targets Collision is.

``` lua
function drawline()
   if (getPedTargetStart(localPlayer)) then --Checks if there is a Point to start From.

      local x,y,z = getPedTargetStart(localPlayer) -- Gets the Point to start From.
      local sx,sy,sz = getPedTargetCollision(localPlayer) -- Gets the Point where the Targets Collision is.

      dxDrawLine3D(x,y,z,sx,sy,sz) -- Draws the Line
   end
end
addEventHandler("onClientPreRender",getRootElement(),drawline) -- Adds the Handler.
```

See Also
--------
