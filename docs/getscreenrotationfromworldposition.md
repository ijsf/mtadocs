This function returns a screen relative rotation to a world position. The returned rotation can be used in [dxDrawImage](/docs/dxdrawimage.md "wikilink")

Syntax
------

``` lua
float getScreenRotationFromWorldPosition( float targetX, float targetY, float targetZ )
```

### Required Arguments

-   **targetX**: The target world X position
-   **targetY**: The target world Y position
-   **targetZ**: The target world Z position

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
function getScreenRotationFromWorldPosition( targetX, targetY, targetZ )
    -- Get camera position and rotation
    local camX, camY, _, lookAtX, lookAtY = getCameraMatrix()
    local camRotZ = math.atan2 ( ( lookAtX - camX ), ( lookAtY - camY ) )

    -- Calc direction to
    local dirX = targetX - camX
    local dirY = targetY - camY

    -- Calc rotation to
    local dirRotZ = math.atan2(dirX,dirY)

    -- Calc relative rotation to
    local relRotZ = dirRotZ - camRotZ

    -- Return rotation in degrees
    return math.deg(relRotZ)
end
```

</section>
Example
-------

This example draws an arrow which points to the centre of the map.

``` lua
addEventHandler('onClientRender', root,
    function ()
        local rotation = getScreenRotationFromWorldPosition( 0, 0, 0 )
        dxDrawImage( 100,100, 100,100, "arrow.png", rotation )
    end
)
```

See Also
--------
