This event is triggered when a ped is killed or dies. It is not triggered for players.

Parameters
----------

``` lua
int totalAmmo, element killer, int killerWeapon, int bodypart, bool stealth
```

-   **totalAmmo**: an integer representing the total ammo the victim had when he died.
-   **killer**: an [element](/docs/element.md "wikilink") representing the player or vehicle who was the killer. If there was no killer this is *false*.
-   **killerWeapon**: an integer representing the [killer weapon](/docs/Weapons.md "wikilink") or the [death reason](/Death_Reasons.md "wikilink").
-   **bodypart**: an integer representing the bodypart ID the victim was hit on when he died.

-   **stealth**: boolean value representing whether or not this was a stealth kill

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [ped](/ped.md "wikilink") that died or got killed.

Example
-------

This example outputs to the console that the ped is now dead.

``` lua
ped1 = createPed(112, 0, 0, 0) --Create our Ped
function died()
    outputConsole("Your Ped is dead now!")
end
addEventHandler("onPedWasted", ped1, died) --Add the Event when ped1 dies
```

See Also
--------
