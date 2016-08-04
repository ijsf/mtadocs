This function allows retrieval of the position where a ped's target range ends, when he is aiming with a weapon.

Syntax
------

``` lua
float float float getPedTargetEnd ( ped targetingPed )
```

### Required Arguments

-   **targetingPed:** the ped who is targeting whose target end you wish to retrieve

### Returns

Returns three floats, *x*,*y*,*z*, representing the position where the ped's target ends according to his range, or *false* if it was unsuccessful.

Example
-------

This Example draws a line from where the Ped´s Target Starts to the Point where the Target Ends

``` lua
addEventHandler("onClientPreRender", root,  -- Adds the Handler
    function ()
        if getPedTargetStart(localPlayer) then --Checks if there is a Point to start From.

        local x, y, z = getPedTargetStart(localPlayer) -- Gets the Point to start From
        local sx, sy, sz = getPedTargetEnd(localPlayer) -- Gets the Point where the Target Ends

        dxDrawLine3D(x, y, z, sx, sy, sz) -- Draws the Line
    end
end
)
```

See Also
--------
