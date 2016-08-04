This function gets the wind velocity in San Andreas.

Syntax
------

``` lua
int, int, int getWindVelocity ( )
```

### Returns

-   **velocityX**: The velocity on the x-coordinate or false if the wind velocity is default.
-   **velocityY**: The velocity on the y-coordinate or nil if the wind velocity is default.
-   **velocityZ**: The velocity on the z-coordinate or nil if the wind velocity is default.

Example
-------

This example returns the wind velocity to a player if they use the command 'getwindvelocity'.

``` lua
function commandGetWindVelocity(player, command)
   local vx, vy, vz = getWindVelocity()
   if (vx) then
       outputChatBox("Wind Velocity X:"..vx.." Y:"..vy.." Z:"..vz, player, 255, 255, 0)
   else
       outputChatBox("Wind velocity is default.", player, 255, 255, 0)
   end
end
addCommandHandler("getwindvelocity", commandGetWindVelocity)
```

See Also
--------
