This event is triggered when a player spawns at a spawnpoint.

Syntax
------

``` lua
void onSpawnpointUse ( player player ) 
```

Variables
---------

-   The [source](/event_system#Event_source.md "wikilink") of this event refers to the spawnpoint that was used when a player spawned
-   **player**: A player element representing the player who spawned at the source spawnpoint.

Example
-------

This example plays a sound when a player spawns

``` lua
function spawnUse ( player ) --when a player spawns
    playSoundFrontEnd ( player, 16 ) --play a sound for him
end
addEventHandler ( "onSpawnpointUse", getElementRoot(), spawnUse ) --add an event for onSpawnpointUse
```
