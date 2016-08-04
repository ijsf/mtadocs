This function allows retrieval of the position a ped's target range begins, when he is aiming with a weapon.

Syntax
------

``` lua
float float float getPedTargetStart ( ped targetingPed )
```

### Required Arguments

-   **targetingPed:** The ped whose target start you wish to retrieve

### Returns

Returns three floats, x,y,z, representing the position where the ped's target starts, or *false* if it was unsuccessful.

Example
-------

This Example draws a line from where the Ped´s Target Starts to the Point where the Target Ends

``` lua
function drawline()
   if (getPedTargetStart(localPlayer)) then --Checks if there is a Point to start From.

      local x,y,z = getPedTargetStart(localPlayer) -- Gets the Point to start From
      local sx,sy,sz = getPedTargetEnd(localPlayer) -- Gets the Point where the Target Ends

      dxDrawLine3D(x,y,z,sx,sy,sz) -- Draws the Line
   end
end
addEventHandler("onClientPreRender",getRootElement(),drawline) -- Adds the Handler
```

See Also
--------
