<lowercasetitle/>

This function gets a team from it's few players. **Note:** If 2 teams has the same count, then the first one found will be returned!

Syntax
------

``` lua
team fewPlayersOnTeams ( element team1,element team2)
```

### Return

Returns a [team](/team.md "wikilink") else false.

Code
----

``` lua
function FewPlayersOnTeams(team1,team2)
    if (isElement(team1) and getElementType(team1) == "team") and (isElement(team2) and getElementType(team2) == "team")  then
        local team1C = countPlayersInTeam (team1)
        local team2C = countPlayersInTeam (team2)
        if team1C == team2C then return team1
        else
            if team1C == math.min(team1C,team2C) then
                return team1
                else
                return team2
            end
         end
    end
        return false
end
```

Example
-------

<section name="Example" class="server" show="true">
``` lua


function setPlayerToTeam(source)
local redteam = getTeamFromName ( "Red" )
local blueteam = getTeamFromName ( "Blue" )
    if redteam and blueteam then
        local theteam = fewPlayersOnTeams(redteam,blueteam)
     if theteam then
        setPlayerTeam(source,theteam)
    local PlayerName = getPlayerName ( source )
    outputChatBox ( "  " .. joinedPlayerName .. "  Joined "..getTeamName(theteam).." team !" , root, 255, 255, 255 )
     end
        else
createTeam ("Red",255,0,0)
createTeam ("Blue",0,0,255)
setPlayerToTeam(source)
    end
end
addEventHandler ( "onPlayerJoin", getRootElement(), setPlayerToTeam )
```

</section>
Author: Booo

See Also
--------
