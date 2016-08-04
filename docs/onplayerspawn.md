This event is called when a player spawns.

Parameters
----------

``` lua
float posX, float posY, float posZ, float spawnRotation, team theTeam, int theSkin, int theInterior, int theDimension
```

-   **posX**: The X position the player spawned at
-   **posY**: The Y position the player spawned at
-   **posZ**: The Z position the player spawned at
-   **spawnRotation**: The rotation the player spawned with
-   **theTeam**: The team the player spawned with
-   **theSkin**: The skin / model the player spawned with
-   **theInterior**: The interior the player spawned in
-   **theDimension**: The dimension the player spawned in

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/docs/player.md "wikilink") that just spawned.

Example
-------

This example plays a sound when a player spawns.

``` lua
-- when a player spawns,
function player_Spawn ( posX, posY, posZ, spawnRotation, theTeam, theSkin, theInterior, theDimension )
    -- play a frontend sound for him
    playSoundFrontEnd ( source, 16 )
end
-- add the player_Spawn function as a handler for onPlayerSpawn
addEventHandler ( "onPlayerSpawn", getRootElement(), player_Spawn )
```
