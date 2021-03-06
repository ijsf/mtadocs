This event is called when ped shoots a weapon. This does not trigger for projectiles based, or melee weapons.

Parameters
----------

``` lua
 int weapon, int ammo, int ammoInClip, float hitX, float hitY, float hitZ, element hitElement
```

-   **weapon**: an [int](/docs/int.md "wikilink") representing [weapon](/docs/weapons.md "wikilink") used for making a shot.
-   **ammo**: an [int](/docs/int.md "wikilink") ammount of ammo left for this weapon type.
-   **ammoInClip**: an [int](/docs/int.md "wikilink") ammount of ammo left for this weapon type in clip.
-   **hitX**, **hitY**, **hitZ**: [float](/docs/float.md "wikilink") world coordinates representing a hit point.
-   **hitElement**: an [element](/docs/element.md "wikilink") which was hit by a shot.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [ped](/docs/ped.md "wikilink") who fired the weapon.

Example
-------

``` lua
addEventHandler("onClientPedWeaponFire", root,
     function(weapon, ammo, ammoInClip, hitX, hitY, hitZ, hitElement)
          if isElement(hitElement) and getElementType(hitElement) == "player" then
               outputChatBox("You hit " .. getPlayerName(hitElement), 0, 255, 0)
          end
     end
)
```

</section>
See Also
--------

### Client ped events

### Client event functions
