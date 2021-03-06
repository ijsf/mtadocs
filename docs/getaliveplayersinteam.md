<lowercasetitle></lowercasetitle>

This function returns a table of the alive players in a team.

Syntax
------

``` lua
table getAlivePlayersInTeam ( element theTeam )
```

### Required Arguments

-   **theTeam**: The element of the team where you want to get the alive players from.

### Optional Arguments

Code
----

<section name="Serverside Script" class="server" show="true">
``` lua
function getAlivePlayersInTeam(theTeam)
    local theTable = { }
    local players = getPlayersInTeam(theTeam)

    for i,v in pairs(players) do
      if not isPedDead(v) then
        theTable[#theTable+1]=v
      end
    end
  
    return theTable
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example get's the alive players from the team “MTA”.

``` lua
function getAlivePlayersInTeam(theTeam)
    local theTable = { }
    local players = getPlayersInTeam(theTeam)

    for i,v in pairs(players) do
        if not isPedDead(v) then
            theTable[#theTable+1]=v
        end
    end

    return theTable
end

mta = createTeam("MTA",255,100,0)

-- define the command handler function
function getThePlayers(thePlayer)
    local count = #getAlivePlayersInTeam(mta) or 0 -- get the alive players.

    outputChatBox("MTA team has ".. tonumber(count) .." players alive.",thePlayer)
end
-- add the command handler
addCommandHandler("alive",getThePlayers)
```

</section>
Author(s): Castillo, Karlis

See Also
--------
