This allows you to change the RGB color mixture in the name tags of players.

Syntax
------

``` lua
bool setPlayerNametagColor ( player thePlayer, int r, int g, int b )
```

### Required Arguments

-   **thePlayer:** The player whose name tag text you wish to change the color of
-   **r:** The amount of red you want in the mixture of RGB (0-255 is valid)
-   **g:** The amount of green you want in the mixture of RGB (0-255 is valid)
-   **b:** The amount of blue you want in the mixture of RGB (0-255 is valid)

### Returns

Returns *true* if the function was successful, *false* otherwise.

Example
-------

This will allow a player to change the RGB color mixture of their nickname. Valid RGB is between 0-255.

``` lua
-- The handler function for the console command
function nametagColorChange ( thePlayer, commandName, r, g, b )
    -- Apply the new color mix of RGB to the command handler activator
    setPlayerNametagColor ( thePlayer, r, g, b )
end
-- This is a command handler that activates on text "nametagcolor" in the console. It also asks 
-- the player to provide values for the extra parameters r, g, b after the command name. These will 
-- be the new color mix of RGB to apply to the player's name tag.
addCommandHandler ( "nametagcolor", nametagColorChange )
```

See Also
--------
