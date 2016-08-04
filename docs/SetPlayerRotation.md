This function allows you to set the current rotation of the specified player.

Syntax
------

``` lua
bool setPlayerRotation ( player thePlayer, float rotation )         
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") to set the rotation of
-   **rotation:** A [float](/float.md "wikilink") specifying the desired rotation in degrees.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

This example allows a player to type the command 'disco', which will result in the player being rotated to a random direction every 1 second, infinite times.

``` lua
function discoTime ( player )
     -- Randomly choose a new player rotation and set it
     newRotation = math.random ( 0, 360 )
     setPlayerRotation ( player, newRotation )
end

function initiateDiscoMode ( player, commandName )
     --Trigger a random change in player rotation every second
     --Send the stored 'activating player' to the discoTime
     --function, so his rotation will be changed.
     setTimer (discoTime, 1000, 0, player )
end
addCommandHandler ( "disco", initiateDiscoMode )
```

See Also
--------
