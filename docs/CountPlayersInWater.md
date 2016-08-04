Syntax
------

``` lua
int countPlayersInWater( player thePlayer )
```

### Required Arguments

-   **thePlayer:** the water to get the count from it.

### Returns

Return a number of players in the water

Code
----

<section name="Function source" class="server" show="true">
``` lua
function countPlayersInWater(Water)
    local count = 0
    if Water and getElementType(Water) == "player" then
        for i,player in ipairs(getElementsByType("player")) do
            if isPlayerInWater(player,Water) then
                count = count + 1
            end
        end
    end
    return count
end
```

</section>
.

Example
-------

<section name="Example" class="server" show="true">
``` lua
function getPlayersWater(player)
local pl = countPlayersInWater(player)
outputChatBox("Players in Water [ "..pl.." ] !",player)
end
addCommandHandler("getPlayerInWater",getPlayersWater)
```

</section>
Created By **ProGamer**.
