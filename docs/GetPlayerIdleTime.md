This function gets the amount of time in milliseconds that a players position has not changed.

Syntax
------

``` lua
int getPlayerIdleTime ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/player.md "wikilink") you wish to get the idle time of.

### Returns

Returns the amount of **time in milliseconds** that a player has been idle, **false** otherwise.

Example
-------

<section name="Serverside example" class="server" show="true">
This example will kick a player if they don't move for 5 minutes and the resource has access to “function.kickPlayer”

``` lua
function checkAFKPlayers()
    for index, thePlayer in ipairs(getElementsByType("player"))do -- Loop all online players
        if (getPlayerIdleTime(thePlayer) > 300000) then -- Player hasn't moved for 300,000ms (5 minutes)
            kickPlayer(thePlayer, "Idle for 5 minutes") -- Kick the idle player
        end
    end
end
setTimer(checkAFKPlayers, 30000, 0) -- Timer to execute every 30 seconds, checking for idlers
```

</section>
Requirements
------------

See Also
--------
