This event is triggered when a pickup is spawned or respawned.

Parameters
----------

This event has no arguments

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [pickup](/docs/pickup.md "wikilink") that just spawned or respawned.

Example
-------

This example get's the area and city name when a pickup spawns and outputs it to all the players.

``` lua
function outputSpawn ()
    local area = getElementZoneName ( source ) -- Get the area name where the pickup spawned.
    local city = getElementZoneName ( source, true ) -- Get the city name where the pickup spawned.
    outputChatBox ( "A pickup has spawned in " .. area .. " ( " .. city .. " )", getRootElement(), 255, 0, 0 ) -- Output the pickup spawn.
end
addEventHandler ( "onPickupSpawn", getRootElement(), outputSpawn ) -- Trigger the function when a pickup spawns.
```
