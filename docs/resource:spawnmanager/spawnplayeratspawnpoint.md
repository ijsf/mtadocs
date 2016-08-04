This function spawns the player at a spawnpoint.

Syntax
------

``` lua
bool spawnPlayerAtSpawnpoint ( player thePlayer, [spawnpoint theSpawnpoint = random, bool useWaves ] )             
```

### Required Arguments

-   **thePlayer:** the player to spawn

### Optional Arguments

-   **theSpawnpoint:** the spawnpoint element at which to spawn the player. If this is not specified, or *false* is passed, a random spawnpoint will be used.
-   **useWaves:** Specifies whether spawn waves will be used from [setSpawnWave](/docs/resource-spawnmanager/setspawnwave.md "wikilink"). If no wave has been set, this will be ignored.

### Returns

Returns *true* if the player was spawned successfully, *false* otherwise.

Example
-------

This example spawns all the players in the map at the first spawnpoint there is.

``` lua
-- Get a table of all the players
players = getElementsByType ( "player" )
-- Get a table of all the spawnpoints
spawnpoints = getElementsByType ( "spawnpoint" )
-- Go through every player
for playerKey, playerValue in players do
    -- Spawn them at the first spawnpoint
    call(getResourceFromName("spawnmanager"), "spawnPlayerAtSpawnpoint", playerValue, spawnpoints[1] )
end
```
