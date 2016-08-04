This function returns a table of all the alive players on the server. Opposite function of [getDeadPlayers](/docs/getdeadplayers.md "wikilink").

Syntax
------

``` lua
table getAlivePlayers ( )
```

### Returns

Returns a table of all the alive players.

Example
-------

This example prints a list of all alive players in a “name, name2, name3” format. If no players are alive then it outputs “none”.

``` lua
-- Print a list of all the alive players
alivePlayers = getAlivePlayers ()
if ( alivePlayers ) then -- if we got the table
    alivePlayersList = "none"
    -- Loop through the table
    for playerKey, playerValue in ipairs(alivePlayers) do
        -- add their name to the list
        if ( alivePlayersList == "none" ) then
            alivePlayersList = getPlayerName ( playerValue )
        else
            alivePlayersList = alivePlayersList .. ", " .. getPlayerName ( playerValue )
        end
    end
    outputChatBox ( "Alive Players: " .. alivePlayersList )    
end
```

See Also
--------

[ru:getAlivePlayers](/docs/ru-getaliveplayers.md "wikilink")
