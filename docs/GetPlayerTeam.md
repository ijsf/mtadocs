This function gets the current [team](/team.md "wikilink") a [player](/player.md "wikilink") is on.

Syntax
------

``` lua
team getPlayerTeam ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/player.md "wikilink") whose team you want to find out.

### Returns

Returns a *team* element representing the team the player is on, *false* if the player is not part of a team.

Example
-------

<section name="Server" class="server" show="true">
This example finds the team a player is on, and then changes its name.

``` lua
function teamName ( source, key, newTeamName )
    local playerTeam = getPlayerTeam ( source )          -- get the player's team
    if ( playerTeam ) then                               -- if he's on a team
        local oldTeamName = getTeamName ( playerTeam )   -- get the team's current name
        setTeamName ( playerTeam, newTeamName )          -- change its name
        outputChatBox ( "Changed " .. getPlayerName ( source ).."'s team name from " .. oldTeamName .. " to " .. newTeamName )
    else
        outputChatBox ( getPlayerName ( source ) .. " isn't on a team" )
    end
end
addCommandHandler ( "teamname", teamName )
```

</section>
See Also
--------
