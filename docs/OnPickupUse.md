This event is triggered when a [player](/docs/player.md "wikilink") stands on a [pickup](/pickup.md "wikilink") while not in a [vehicle](/vehicle.md "wikilink"). Pickups use [colshapes](/colshape.md "wikilink"), you can get the [colshape](/colshape.md "wikilink") of the [pickup](/pickup.md "wikilink") with [getElementColShape](/getElementColShape.md "wikilink") and use [colshape](/colshape.md "wikilink") [events](/event.md "wikilink") to it

Parameters
----------

``` lua
player playerWhoUsed
```

-   **playerWhoUsed**: A player element refering to the player who used the pickup

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [pickup](/pickup.md "wikilink") that is getting used by the player.

### Canceling

If this event is [canceled](/docs/Event_system_#Canceling.md "wikilink"), the player will not be given the item they picked up.

Example
-------

This example announces whena player picks up a pickup

``` lua
function pickupUse ( thePlayer )
    outputChatBox ( getPlayerName ( thePlayer ) .. " picked up a pickup!" )
end
addEventHandler ( "onPickupUse", getRootElement(), pickupUse )
```
