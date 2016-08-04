This event is triggered whenever a player's equipped weapon **slot** changes. This means giveWeapon and takeWeapon will trigger this function if the equipped slot is forced to change.

Parameters
----------

``` lua
int previousWeaponID, int currentWeaponID
```

-   **previousWeaponID**: An [integer](/int.md "wikilink") representing the [weapon](/weapons.md "wikilink") that was switched from
-   **currentWeaponID**: An [integer](/int.md "wikilink") representing the [weapon](/weapons.md "wikilink") that was switched to

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that switched his weapon.

Example
-------

This example disables use of the minigun upon switch. It should be noted that this can be done more efficiently clientside.

``` lua
WeaponID = {
    [31] = true,
    [36] = true,
    [38] = true,
}

--add an event handler for onPlayerWeaponSwitch
addEventHandler ( 'onPlayerWeaponSwitch', getRootElement ( ),
    function ( previousWeaponID, currentWeaponID )
        if ( WeaponID[currentWeaponID] ) then
            toggleControl ( source, 'fire', false ) --disable the fire button
        else
            toggleControl ( source, 'fire', true ) --enable it
        end
    end
)
```
