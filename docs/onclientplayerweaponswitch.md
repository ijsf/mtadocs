This event is triggered whenever the local player's equipped weapon **slot** changes. This means giveWeapon and takeWeapon will trigger this function if the equipped slot is forced to change.

Parameters
----------

``` lua
int previousWeaponSlot, int currentWeaponSlot
```

-   **previousWeaponSlot**: An integer representing the previous weapon slot the player had before he switched.
-   **currentWeaponSlot**: An integer representing the new weapon slot the player has.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") who changed his weapon. (Local player only)

Cancel effect
-------------

If this event is canceled, then the weapon will not be switched.

Example
-------

This example disables the use of aiming for the minigun.

``` lua
function disableMinigunOnSwitch ( prevSlot, newSlot )
    if getPedWeapon(getLocalPlayer(),newSlot) == 38 then --if the switched weapon is the minigun
        toggleControl ( "aim_weapon", false ) --disable the aim button
    else --if it isnt the minigun
        toggleControl ( "aim_weapon", true ) --renable the aim button
    end
end
addEventHandler ( "onClientPlayerWeaponSwitch", getRootElement(), disableMinigunOnSwitch )
```

See Also
--------

### Client player events

### Client event functions
