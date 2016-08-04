Spawnmanager is a resource that provides some default spawning functions. It provides ideal conditions for gamemodes which require fairly basic spawning systems, and uses the <spawnpoint/> element for all its functions.

Spawnmanager also offers basic support for a *waves* spawning system - which involves spawning multiple players at regular periods of time. Spawnmanager does not internally support delayed spawning, though [setTimer](/docs/settimer.md "wikilink") can be used in conjunction with [spawnPlayerAtSpawnpoint](/docs/resource:spawnmanager/spawnplayeratspawnpoint.md "wikilink") to achieve this.

Functions
---------

The following functions are exported as part of spawnmanager:

-   [createSpawnpoint](/docs/resource:spawnmanager/createspawnpoint.md "wikilink")
-   [getSpawnpointRotation](/docs/resource:spawnmanager/getspawnpointrotation.md "wikilink")
-   [getSpawnpointSkin](/docs/resource:spawnmanager/getspawnpointskin.md "wikilink")
-   [getSpawnpointTeam](/docs/resource:spawnmanager/getspawnpointteam.md "wikilink")
-   [setSpawnpointRotation](/docs/resource:spawnmanager/setspawnpointrotation.md "wikilink")
-   [setSpawnpointSkin](/docs/resource:spawnmanager/setspawnpointskin.md "wikilink")
-   [setSpawnpointTeam](/docs/resource:spawnmanager/setspawnpointteam.md "wikilink")
-   [spawnPlayerAtSpawnpoint](/docs/resource:spawnmanager/spawnplayeratspawnpoint.md "wikilink")
-   [setSpawnWave](/docs/resource:spawnmanager/setspawnwave.md "wikilink")

Events
------

The following events are provided:

-   [onSpawnpointUse](/docs/resource:spawnmanager/onspawnpointuse.md "wikilink")

[ru:<Resource:Spawnmanager>](/docs/ru:resource:spawnmanager.md "wikilink")
