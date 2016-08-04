This function is used to determine whether or not a player is currently in water. Player is in water only if breath bar appears.

Syntax
------

``` lua
bool isPlayerInWater ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") you are checking.

### Returns

Returns *true* if the player is in water, *false* otherwise.

Example
-------

<section name="Serverside example" class="server" show="true">
This example shows all players that are in water in a list to the player who enters the 'playersInWater' command.

     [lua]
    function showPlayersInWater(sourcePlayer, command)
        local players = getElementsByType("player")
        local list = ""
        for k,v in ipairs(players) do
            if isPlayerInWater(v) then
                list = list .. " " .. getClientName(v)
            end
        end
        outputChatBox("Players pretending to be trouts: " .. list, sourcePlayer)
    end
    addCommandHandler("playersInWater", showPlayersInWater)

</section>
See Also
--------
