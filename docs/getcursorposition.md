This function gets the current position of the mouse cursor. Note that for performance reasons, the world position returned is always 300 units away. If you want the exact world point (similar to [onClientClick](/docs/onclientclick.md "wikilink")), use [processLineOfSight](/docs/processlineofsight.md "wikilink") between the camera position and the worldX/Y/Z result of this function. (See example below)

Syntax
------

``` lua
float float float float float getCursorPosition ( )
```

### Returns

Returns 5 values: *cursorX*, *cursorY*, *worldX*, *worldY*, *worldZ*. The first two values are the 2D relative screen coordinates of the cursor: *cursorX* goes from 0 (left side of the screen) to 1 (right side), *cursorY* goes from 0 (top) to 1 (bottom). The 3 values that follow are the 3D world map coordinates that the cursor points at. If the cursor isn't showing, returns *false* as the first value.

### Issues

Example
-------

This example prints your cursors current world coordinates and relative screen coordinates to chatbox after typing *cursorpos*.

``` lua
function cursorInfo()
   local showing = isCursorShowing ()
   if showing then -- if the cursor is showing
      local screenx, screeny, worldx, worldy, worldz = getCursorPosition()

      outputChatBox( string.format( "Cursor screen position (relative): X=%.4f Y=%.4f", screenx, screeny ) ) -- make the accuracy of floats 4 decimals
      outputChatBox( string.format( "Cursor world position: X=%.4f Y=%.4f Z=%.4f", worldx, worldy, worldz ) ) -- make the accuracy of floats 4 decimals accurate
   else
      outputChatBox( "Your cursor is not showing." )
   end
end
addCommandHandler( "cursorpos", cursorInfo )
```

This (untested) example uses [processLineOfSight](/docs/processlineofsight.md "wikilink") to calculate the exact world location:

``` lua
addEventHandler( "onClientRender", root,
    function()
        if isCursorShowing() then
            local screenx, screeny, worldx, worldy, worldz = getCursorPosition()
            local px, py, pz = getCameraMatrix()
            local hit, x, y, z, elementHit = processLineOfSight ( px, py, pz, worldx, worldy, worldz )

            if hit then
                dxDrawText( "Cursor at " .. x .. " " .. y .. " " ..  z, 200, 200 )
                if elementHit then
                    dxDrawText( "Hit element " .. getElementType(elementHit), 200, 220 )
                end
            end
        end
    end
)
```

See Also
--------
