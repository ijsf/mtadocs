This function adds a [player](/docs/player.md "wikilink") to an existing [team](/docs/team.md "wikilink"). The player will automatically be removed from his current team if he's on one.

Syntax
------

``` lua
bool setPlayerTeam ( player thePlayer, team theTeam )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") you wish to add to a team.
-   **theTeam:** The [team](/docs/team.md "wikilink") you want to add the player to, or *nil* if you wish to unassign a player from his team.

### Returns

Returns *true* if the player was successfully added to the specified team or removed from his previous one, *false* otherwise.

Example
-------

This example adds a command to create a new team for a player, then add him to it. It also adds a command to remove him from his team.

``` lua
function assignNewTeam ( source, commandName, teamName )
  local theTeam = createTeam ( teamName )  -- create a new team with the specified name
  if theTeam then                          -- if it was successfully created
    setPlayerTeam ( source, theTeam )    -- add the player to the new team
  end
end
addCommandHandler ( "gimmeateam", assignNewTeam )

function unassignTeam ( source, commandName )
  local theTeam = getPlayerTeam ( source )  -- Check if the player is on a team
  if theTeam then                          -- this player is on a team, so we can remove them from it
    setPlayerTeam ( source, nil )    -- remove the player from the current team
  end
end
addCommandHandler ( "takeawaymyteam", unassignTeam )
```

See Also
--------
