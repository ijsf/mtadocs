This function sets the spawn wave time. This can be used in conjunction with [spawnPlayerAtSpawnpoint](/docs/resource-spawnmanager/spawnplayeratspawnpoint.md "wikilink") to spawn players when a wave is reached.

Syntax
------

``` lua
bool setSpawnWave ( bool enabled, [ float time = 15000 ] )             
```

### Required Arguments

-   **enabled:** A bool representing whether to enable waves or not

### Optional Arguments

-   **time:** The time, in milliseconds, of how regularly a spawn wave occurs.

### Returns

Returns *true* if the spawnwave was enabled or disabled, or *false* if a bad argument was specified.

Example
-------

This page lacks an example

``` lua
--add an example here.
```
