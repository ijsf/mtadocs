This event is called when a player fires a weapon. This does not trigger for projectiles, melee weapons, or camera.

Parameters
----------

``` lua
int weapon, int ammo, int ammoInClip, float hitX, float hitY, float hitZ, element hitElement, float startX, float startY, float startZ
```

-   **weapon**: an [int](/docs/int.md "wikilink") representing [weapon](/weapons.md "wikilink") used for making a shot.
-   **ammo**: an [int](/docs/int.md "wikilink") amount of ammo left for this weapon type.
-   **ammoInClip**: an [int](/docs/int.md "wikilink") amount of ammo left for this weapon type in clip.
-   **hitX**, **hitY**, **hitZ**: [float](/docs/float.md "wikilink") world coordinates representing a hit point.
-   **hitElement**: an [element](/docs/element.md "wikilink") which was hit by a shot.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the streamed in [player](/player.md "wikilink") who fired the weapon.

Example
-------

This example sends a warning to the local player if they shoot another player with a minigun.

``` lua
--First, we create a function for the event handler to use.
function onClientPlayerWeaponFireFunc(weapon, ammo, ammoInClip, hitX, hitY, hitZ, hitElement )
    if weapon == 38 and getElementType(hitElement)=="player" then -- If the player shoots with a minigun, and hits another player...
         outputChatBox ( "Don't kill people with minigun, it's lame!", 255, 0, 0 ) -- We output a warning to him.
    end
end
-- Add this as a handler so that the function will be triggered every time the local player fires.
addEventHandler ( "onClientPlayerWeaponFire", getLocalPlayer(), onClientPlayerWeaponFireFunc )
```

This example makes the Shotgun fire explosive rounds.

``` lua
function onClientPlayerWeaponFireFunc(weapon, ammo, ammoInClip, hitX, hitY, hitZ, hitElement)
    if (weapon == 25) then -- If the player shoots with a shotgun
        createExplosion(hitX, hitY, hitZ, 12, true, 0, true) -- Creates a tiny explosion where the bullet hit.
    end
end
-- Add this as a handler so that the function will be triggered every time a player fires.
addEventHandler("onClientPlayerWeaponFire", root, onClientPlayerWeaponFireFunc)
```

Issues
------

See Also
--------

### Client player events

### Client event functions
