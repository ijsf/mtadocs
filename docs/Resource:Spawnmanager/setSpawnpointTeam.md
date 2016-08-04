This function sets the team that players will be added to when they spawn at the specified spawnpoint. Please note that although players will be removed from any team they were previously in when spawning at a team spawnpoint, spawning at a spawnpoint with no team associated to it won't remove a player from their team.

Syntax
------

``` lua
bool setSpawnpointTeam ( spawnpoint spawn, [ team theTeam ] )
```

### Required Arguments

-   **spawn:** The spawnpoint element you want to change team of.

### Optional Arguments

-   **theTeam:** A [team](/docs/team.md "wikilink") element representing the team players will join on spawn. If this isn't specified, the spawnpoint is unlinked to any team it was associated to.

### Returns

Returns *true* if the team was successfully set, *false* if invalid arguments were passed.

Example
-------

This page lacks an example

``` lua
--add an example here
```
