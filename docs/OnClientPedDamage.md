This event is triggered whenever a [ped](/ped.md "wikilink") is damaged.

Parameters
----------

``` lua
element attacker, int weapon, int bodypart [, float loss ]
```

-   **attacker**: A [player](/player.md "wikilink") [element](/element.md "wikilink") representing the attacker or [vehicle](/vehicle.md "wikilink") [element](/element.md "wikilink") (when a ped falls of a bike).
-   **weapon**: An integer representing the weapon ID the attacker used
-   **bodypart**: An integer representing the bodypart the ped was damaged

-   **loss**: A float representing the percentage of health the ped lost.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [ped](/ped.md "wikilink") that got damaged

Cancel effect
-------------

If this event is [canceled](/Event_system#Canceling.md "wikilink"), then any damaging effects to the ped will cease.

Example
-------

This example cancels any damage done to peds

``` lua
function cancelPedDamage ( attacker )
    cancelEvent() -- cancel any damage done to peds
end
addEventHandler ( "onClientPedDamage", getRootElement(), cancelPedDamage )
```

Issues
------

See Also
--------

### Client ped events

### Client event functions
