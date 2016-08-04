This allows you to retrieve what fighting style a player is currently using.

Syntax
------

``` lua
int getPlayerFightingStyle ( player thePlayer ) 
```

### Required Arguments

-   **thePlayer:** The player whose current fighting style ID you wish to retrieve

### Returns

Returns the player's current fighting style as an integer ID, *false* if it fails to retrieve a value.

Example
-------

This will allow any player to check what fighting style they are currently using, by typing the 'getfightingstyle' command.

``` lua
function getPlayerFightStyle ( thePlayer, commandName )
    local playerstyle = getPlayerFightingStyle ( thePlayer )   -- store the fighting style in a variable
    outputChatBox ( tostring(playerstyle), thePlayer )         -- output it to the player
end
addCommandHandler ( "getfightingstyle", getPlayerFightStyle )
```

See Also
--------
