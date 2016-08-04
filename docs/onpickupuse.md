This event is triggered when a [player](/docs/player.md "wikilink") stands on a [pickup](/docs/pickup.md "wikilink") while not in a [vehicle](/docs/vehicle.md "wikilink"). Pickups use [colshapes](/docs/colshape.md "wikilink"), you can get the [colshape](/docs/colshape.md "wikilink") of the [pickup](/docs/pickup.md "wikilink") with [getElementColShape](/docs/getelementcolshape.md "wikilink") and use [colshape](/docs/colshape.md "wikilink") [events](/docs/event.md "wikilink") to it

Parameters
----------

``` lua
player playerWhoUsed
```

-   **playerWhoUsed**: A player element refering to the player who used the pickup

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [pickup](/docs/pickup.md "wikilink") that is getting used by the player.

### Canceling

If this event is [canceled](/docs/event_system_#canceling.md "wikilink"), the player will not be given the item they picked up.

Example
-------

This example announces whena player picks up a pickup

``` lua
function pickupUse ( thePlayer )
    outputChatBox ( getPlayerName ( thePlayer ) .. " picked up a pickup!" )
end
addEventHandler ( "onPickupUse", getRootElement(), pickupUse )
```
