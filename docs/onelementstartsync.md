This event is triggered when an element becomes synced by a player.

Parameters
----------

``` lua
player newSyncer
```

-   **newSyncer**: [player](/docs/player.md "wikilink") element representing the player who is now syncing the element

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [element](/docs/element.md "wikilink") that got synced by a player.

Example
-------

When an element receives a new syncer, this example matches the model of the element to the player.

``` lua
function elementStartSync( newSyncer )
    local strElementType = getElementType( source )
    local playerVehicle = getPedOccupiedVehicle( newSyncer )
    if ( strElementType == 'vehicle' ) then
        if ( not playerVehicle ) then return false end
        
        setElementModel( source, getElementModel(playerVehicle) )
    elseif ( strElementType == 'ped' ) then
        setElementModel( source, getElementModel(newSyncer) )
    end
end
addEventHandler ('onElementStartSync', root, elementStartSync)
```
