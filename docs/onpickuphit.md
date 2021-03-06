This event is triggered when a [player](/docs/player.md "wikilink") hits a [pickup](/docs/pickup.md "wikilink").

Parameters
----------

``` lua
player thePlayer
```

-   **thePlayer**: a player [element](/docs/element.md "wikilink") referring to the player who moved over the pickup.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [pickup](/docs/pickup.md "wikilink") that was hit by the player.

Cancel effect
-------------

If this event is [canceled](/docs/event_system#canceling.md "wikilink"), the pickup does not disappear and the player does not receive its bonus.

Example
-------

This example creates a pickup and outputs a message to the chat box when a player walks over it.

``` lua
local aPickup = createPickup ( 10.0, 10.0, 10.0, 2, 31, 3000, 50 ) --Create an M4 weapon pickup when script starts

function pickedUpWeaponCheck ( player )
   outputChatBox ( "You have picked up a M4.", player ) --Display this message in the chat box
end
addEventHandler ( "onPickupHit", aPickup, pickedUpWeaponCheck )
```
