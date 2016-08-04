This event is triggered when an element is no longer synced by a player.

Parameters
----------

``` lua
player oldSyncer
```

-   **oldSyncer**: [player](/docs/player.md "wikilink") element representing the last player who was syncing the element

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [element](/docs/element.md "wikilink") which is no longer synced by a player.

Example
-------

This script creates a vehicle in the center of the map and outputs a message to its old syncer if he is not syncing the vehicle anymore.

``` lua
--create our testing vehicle onResourceStart
addEventHandler ( "onResourceStart", getResourceRootElement( ),
function ( )
    vehicle = createVehicle ( 520, 0, 0, 0 )
end )

function syncStop ( oldSyncer )
    -- check if the element that stopped being synced was our vehicle
    if source == vehicle then
        --tell the player (oldSyncer) he stopped syncing the vehicle
        outputChatBox ( "The vehicle is not being synced by you anymore", oldSyncer )
    end
end
--add the event handler
addEventHandler( "onElementStopSync", getRootElement(), syncStop ) 
```
