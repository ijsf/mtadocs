This event is triggered when a ped switches weapons.

Parameters
----------

``` lua
int previousWeaponID, int currentWeaponID
```

-   **previousWeaponID**: An integer representing the weapon that was switched from
-   **currentWeaponID**: An integer representing the weapon that was switched to

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [ped](/ped.md "wikilink") that switched his weapon.

Example
-------

This example outputs a line to the chat box whenever a ped changes weapons.

``` lua
function weaponSwitch ( previousWeaponID, currentWeaponID )

outputChatBox("A ped switched weapons from " .. previousWeaponID .. " to " .. currentWeaponID .. "!")

end

addEventHandler ( "onPedWeaponSwitch", getRootElement(), weaponSwitch )
```

See Also
--------
