Spawnmanager is a resource that provides some default spawning functions. It provides ideal conditions for gamemodes which require fairly basic spawning systems, and uses the <spawnpoint/> element for all its functions.

Spawnmanager also offers basic support for a *waves* spawning system - which involves spawning multiple players at regular periods of time. Spawnmanager does not internally support delayed spawning, though [setTimer](/docs/setTimer.md "wikilink") can be used in conjunction with [spawnPlayerAtSpawnpoint](/Resource:Spawnmanager/spawnPlayerAtSpawnpoint.md "wikilink") to achieve this.

Functions
---------

The following functions are exported as part of spawnmanager:

-   [createSpawnpoint](/docs/Resource:Spawnmanager/createSpawnpoint.md "wikilink")
-   [getSpawnpointRotation](/docs/Resource:Spawnmanager/getSpawnpointRotation.md "wikilink")
-   [getSpawnpointSkin](/docs/Resource:Spawnmanager/getSpawnpointSkin.md "wikilink")
-   [getSpawnpointTeam](/docs/Resource:Spawnmanager/getSpawnpointTeam.md "wikilink")
-   [setSpawnpointRotation](/docs/Resource:Spawnmanager/setSpawnpointRotation.md "wikilink")
-   [setSpawnpointSkin](/docs/Resource:Spawnmanager/setSpawnpointSkin.md "wikilink")
-   [setSpawnpointTeam](/docs/Resource:Spawnmanager/setSpawnpointTeam.md "wikilink")
-   [spawnPlayerAtSpawnpoint](/docs/Resource:Spawnmanager/spawnPlayerAtSpawnpoint.md "wikilink")
-   [setSpawnWave](/docs/Resource:Spawnmanager/setSpawnWave.md "wikilink")

Events
------

The following events are provided:

-   [onSpawnpointUse](/docs/Resource:Spawnmanager/onSpawnpointUse.md "wikilink")

[ru:<Resource:Spawnmanager>](/docs/ru:Resource:Spawnmanager.md "wikilink")
