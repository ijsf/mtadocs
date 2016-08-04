This event triggers when a [custom weapon](/docs/element/weapon.md "wikilink") fires a shot.

Parameters
----------

``` lua
element hitElement, float posX,  float posY, float posZ, float normalX, float normalY, float normalZ, int materialType, int lighting, int pieceHit
```

-   **hitElement:** the element that was hit
-   **posX:** the position it will hit
-   **posY:** the position it will hit
-   **posZ:** the position it will hit
-   **normalX:** the normal it hit ( see processLineOfSight )
-   **normalY:** the normal it hit ( see processLineOfSight )
-   **normalZ:** the normal it hit ( see processLineOfSight )
-   **materialType:** the material type it hit ( see processLineOfSight )
-   **lighting:** the lighting of the entity it hit ( see processLineOfSight )
-   **pieceHit:** the piece of the entity it hit ( see processLineOfSight )

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the weapon that was fired.

Cancel Effect
-------------

If this event was [canceled](/docs/event_system#canceling.md "wikilink"), then the weapon will not fire.

Example
-------

This example prevents player damage from custom weapons.

``` lua
function noDamageToPlayersFromCustomWeapons(target)
    if target == localPlayer then
        cancelEvent() -- If the weapon hit the player, cancel the shot
    end
end
addEventHandler("onClientWeaponFire", root, noDamageToPlayersFromCustomWeapons)
```

See Also
--------

### Client event functions
