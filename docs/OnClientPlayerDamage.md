This event is triggered whenever a player is damaged.

Parameters
----------

``` lua
element attacker, int weapon, int bodypart [, float loss ]
```

-   **attacker**: A [player](/player.md "wikilink") [element](/element.md "wikilink") representing the attacker or [vehicle](/vehicle.md "wikilink") [element](/element.md "wikilink") (when being run over or falling off a bike).
-   **weapon**: An integer representing the weapon ID the attacker used
-   **bodypart**: An integer representing the bodypart the player was damaged

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that got damaged. (Streamed in players only)

Cancel effect
-------------

If this event is [canceled](/Event_system#Canceling.md "wikilink"), then any damaging effects to the local player will cease.

Example
-------

This example prevents any damage from the minigun.

``` lua
function stopMinigunDamage ( attacker, weapon, bodypart )
    if ( weapon == 38 ) then --if the weapon used was the minigun
        cancelEvent() --cancel the event
    end
end
addEventHandler ( "onClientPlayerDamage", getLocalPlayer(), stopMinigunDamage )
```

Issues
------

See Also
--------

### Client player events

### Client event functions
