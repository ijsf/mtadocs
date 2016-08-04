This function returns the ping of a specified [player](/docs/player.md "wikilink"). The ping is the number of milliseconds that data takes to travel from the player's client to the server or vice versa.

Syntax
------

``` lua
int getPlayerPing ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/docs/player.md "wikilink") whose ping you want to determine.

### Returns

Returns the ping as an [int](/docs/int.md "wikilink"), or *false* if the player is invalid.

Example
-------

<section name="Server" class="server" show="true">
This example checks every players ping every 5 seconds and if it's over 500 they get kicked.

``` lua
function kickPing() -- Creates a function called kickPing
    for i, player in ipairs(getElementsByType("player")) do -- Loop every player
        if (getPlayerPing(player) >= 500) then -- If their ping is over 500
            kickPlayer(player, "Ping over 500!") -- Kick them
        end
    end
end
setTimer(kickPing, 5000, 0) -- Every 5 seconds, the kickPing function is called.
```

</section>
<section name="Client" class="client" show="true">
This example checks the ping of every player entering the 'ping' command and warns him if it's over 100.

``` lua
function checkPing()
        local ping = getPlayerPing(getLocalPlayer())  -- get the ping from the source element (the player who joined)
        if (ping > 100) then                          -- if it's higher than 100...
                outputChatBox("Your ping is pretty high! Please try to lower it if possible.") -- output a message to the player
        end
end
addCommandHandler("ping", checkPing)
```

</section>
See Also
--------

[ru:getPlayerPing](/docs/ru:getplayerping.md "wikilink")
