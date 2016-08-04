This function is for removing a player from his current team.

Syntax
------

``` lua
bool removePlayerFromTeam ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The player you wish to remove from his team.

### Returns

Returns *true* if the player was on a team and was successfully removed it, *false* otherwise.

Example
-------

This example adds two new commands in console. One to create a new team for a player, and another to remove the player from that team

``` lua
function gimmeATeam ( source, key, teamName )
    local newTeam = createTeam ( teamName )  -- create a new team with the specified name
    if ( newTeam ) then                      -- if it was successfully created
        setPlayerTeam ( source, newTeam )  -- add the player to the new team
    end
end
addCommandHandler ( "gimmeateam", gimmeATeam )

function removeMyTeam ( source, key, teamName )
    local myTeam = getPlayerTeam ( source )--get his team
    if ( myTeam ) then --if he does have a team
        setPlayerTeam ( source, nil )      -- remove him from the team
        destroyElement ( myTeam ) --destroy his team
    end
end
addCommandHandler ( "removemyteam", removeMyTeam )
```

See Also
--------
