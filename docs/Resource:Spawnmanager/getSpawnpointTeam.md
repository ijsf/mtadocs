This function returns the [team](/team.md "wikilink") element from a particular spawnpoint.

Syntax
------

``` lua
team getSpawnpointTeam ( spawnpoint spawn )              
```

### Required Arguments

-   **spawn:** A valid spawnpoint element.

### Returns

If the spawnpoint given is valid and has a team, it returns a [team](/team.md "wikilink") element representing the team players will join when spawning there, *false* otherwise.

Example
-------

This example outputs which team, if any, the spawnpoint is associated with when a player spawns.

``` lua
function checkPlayerSpawn ( theSpawnpoint )
    local outString = "Player spawned"
    local spawnTeam
    
    if ( theSpawnpoint ) then
        outString = outString .. " on a spawnpoint"
        
        spawnTeam = call(getResourceFromName("spawnmanager"), "getSpawnpointTeam", theSpawnpoint )
        if ( spawnTeam ) then
            outString = outString .. " for team: " .. getTeamName ( spawnTeam )
        end
    end
    
    outString = outString .. "."
    outputChatBox ( outString )
end
addEventHandler ( "onPlayerSpawn", getRootElement(), checkPlayerSpawn )
```
