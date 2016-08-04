This function returns a [string](/string.md "wikilink") containing the current mode of the player's camera.

Syntax
------

``` lua
string getCameraMode ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The player whose camera mode you wish to obtain.

### Returns

Returns a [string](/string.md "wikilink") with one of two values if successful:

-   **player:** The camera is attached to a player.
-   **fixed:** The camera is in a fixed position.

The function will return *false* if unsuccessful.

Example
-------

This function checks the camera state of a player, by specifying his name:

``` lua
function checkCamera( source, command, targetName )
      local targetPlayer = getPlayerFromNick ( targetName )   -- Get the player using his name
      outputConsole( targetName.."'s camera mode is: "..getCameraMode( targetPlayer ), source )  -- Output the state of player's camera
end
addCommandHandler( "camera", checkCamera )
```

See Also
--------
