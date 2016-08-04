This event is triggered when any player, including a remote player, spawns.

Parameters
----------

``` lua
team hisTeam
```

-   **hisTeam**: A team element representing the team the player spawned on.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that spawned.

Example
-------

This code will create an explosion for the local player when they spawn.

``` lua
function explosionOnSpawn ( )
  -- get the spawned player's position
  local pX, pY, pZ = getElementPosition ( source )
  -- and create an explosion there
  createExplosion ( pX, pY, pZ, 6 )
end
-- add this function as a handler for any player that spawns
addEventHandler ( "onClientPlayerSpawn", getLocalPlayer(), explosionOnSpawn )
```

See Also
--------

### Client player events

### Client event functions
