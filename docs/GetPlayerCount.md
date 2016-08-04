This function returns the number of players currently connected to the server.

Syntax
------

``` lua
int getPlayerCount ( )
```

### Returns

Returns the number of players connected to the server as an [int](/int.md "wikilink").

Example
-------

This example displays a chat message with the number of players connected to the server when a player joins or quits.

``` lua
function playerCount ( )
    outputChatBox ( "There are now " .. getPlayerCount() .. " players on this server!" )
end
addEventHandler ( "onPlayerJoin", getRootElement(), playerCount )
addEventHandler ( "onPlayerQuit", getRootElement(), playerCount )
```

Shared implementation of getPlayerCount
---------------------------------------

*getElementsByType(“player”)* returns a regular-indexed table with every player connected to the server, so by counting how many entries has the table (by using the *\#* operator) we can archieve the same result as this function, but also clientside. However, it's more efficient to use the built-in function serverside. The next function replaces this function accordingly serverside and clientside to work on both.

<section name="Shared (client and server)" class="both" show="true">
``` lua
local originalGetPlayerCount = getPlayerCount -- Store the original getPlayerCount function to a variable

function getPlayerCount()
    -- If originalGetPlayerCount is defined, that means that this function is executed serverside.
    -- The next line returns the result of the original function if it's defined. If not, it counts the number of player elements (to also work clientside).
    return originalGetPlayerCount and originalGetPlayerCount() or #getElementsByType("player")
end
```

</section>
See Also
--------

[ru:getPlayerCount](/ru:getPlayerCount.md "wikilink")
