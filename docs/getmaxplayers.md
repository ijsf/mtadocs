This function returns the maximum number of player slots on the server.

Syntax
------

``` lua
int getMaxPlayers ()
```

### Returns

Returns the maximum number of players allowed on the server.

Example
-------

This example outputs the current number of players together with the maximum number of players when a player joins.

``` lua
function showPlayers()
    outputChatBox("There are "..getPlayerCount().."/"..getMaxPlayers().." players playing.",source) --output a message to the joined player informing the player count and max players.
end
addEventHandler("onPlayerJoin",root,showPlayers) --Add an event handler to call the function when a player joins.
```

See Also
--------
