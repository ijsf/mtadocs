This function can be used to change the syncer ([player](/docs/player.md "wikilink")) of an element. The syncer is the player who is responsible for informing the server about the state of that element - it's position, orientation and other state information. The function can be also used to remove an element's syncer.

Only [vehicle](/docs/vehicle.md "wikilink") and [ped](/ped.md "wikilink") elements can have a syncer, other element types are not currently automatically synced by MTA.

Please note that using this function to change an element's syncer will only last as long as the element is within syncable range of the player. This is within 140 units for vehicles and 100 units for peds. As soon as it becomes impossible for your chosen player to sync the element, another player (or no player) will be automatically selected, and your setting will be lost. With vehicles, the last occupant to leave a vehicle will be selected as the syncer and override any setting you may have made.

Using this function to remove an element's syncer, means no player will be assigned to syncing the element. That will not be changed until setElementSyncer is called again. It should also be noted that certain network changes to an element do not require a syncer. Actions such as destroying an element or explicitly setting the element's position (in a server side script), will still be updated on all clients regardless of this setting.

Syntax
------

``` lua
bool setElementSyncer ( element theElement, player thePlayer )
```

### Required Arguments

-   **theElement:** The [element](/docs/element.md "wikilink") whose syncer you wish to change.
-   **thePlayer:** The [player](/docs/player.md "wikilink") who should be the new syncer of the element. If set to *false*, this element will not have a syncer. If set to *true*, MTA will pick automatically the nearest or most relevant player to that element.

### Returns

Returns *true* if the syncer was changed successfully, *false* if the element passed was not a ped or vehicle.

Example
-------

``` lua
addCommandHandler ( "createMyVehicle", function ( player, command )
    local x, y, z = getElementPosition ( player )
    local myVehicle = createVehicle ( 411, x, y, z )
    setElementSyncer ( myVehicle, player )
end
)
```

See Also
--------
