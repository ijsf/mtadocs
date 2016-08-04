Syntax
------

``` lua
int getPlayersInServer( player thePlayer )
```

### Required Arguments

-   **thePlayer:** the Server to get the count from it.

### Returns

Return a number of players in the Server

Code
----

<section name="Function source" class="server" show="true">
``` lua
function getPlayersInServer ( player )
local Players = 0
    if player and getElementType(player) == "player" then
        for i,player in ipairs(getElementsByType("player")) do
        getPlayerCount(player)
        Players = Players +1
        end
        end
        return Players
        end
```

</section>
.

Example
-------

<section name="Example" class="server" show="true">
this function use for get Players In Server

``` lua
        function countPlayersInServer(player)
        local Player = getPlayersInServer(player)
        outputChatBox(Player.." In Server",player)
        end
        addCommandHandler("Players",countPlayersInServer)
```

</section>
`Created By : `**`ProGamer,79`**
