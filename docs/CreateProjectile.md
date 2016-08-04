This function creates a projectile of the specified type on the specified coordinates.

Syntax
------

``` lua
projectile createProjectile ( element creator, int weaponType [, float posX, float posY, float posZ, float force = 1.0, element target = nil, float rotX, float rotY, float rotZ, float velX, float velY, float velZ, int model ] )
```

### Required Arguments

-   **creator:** The [element](/element.md "wikilink") representing creator of the projectile. In case you want the projectile to be synced for everybody creator must be the local player or his vehicle.
-   **weaponType:** [int](/int.md "wikilink") representing the projectile weaponType (characteristics). Valid IDs are:

### Optional Arguments

-   **posX**, **posY**, **posZ**: [float](/float.md "wikilink") starting coordinates for the projectile. They are coordinates of creator by default.
-   **force**: [float](/float.md "wikilink") representing the starting force for throwable projectiles.
-   **target**: [element](/element.md "wikilink") target used for heat seeking rockets.
-   **rotX**, **rotY**, **rotZ**: [float](/float.md "wikilink") starting rotation for the projectile.
-   **velX**, **velY**, **velZ**: [float](/float.md "wikilink") starting velocity for the projectile.
-   **model**: Integer representing the projectile's model, uses default model for weaponType if not specified.

Returns
-------

Returns a *[projectile](/projectile.md "wikilink")* element if [projectile](/projectile.md "wikilink") creation was successful. Returns *false* if unable to create a [projectile](/projectile.md "wikilink") (wrong weapon ID or projectiles limit was reached).

Example
-------

This example makes a rocket minigun (minigun shooting with rockets).

``` lua
-- This function gets triggered everytime player shoots.
function onClientPlayerWeaponFireFunc(weapon,ammo,ammoInClip,hitX,hitY,hitZ,hitElement)
    if weapon == 38 then -- if source is a local player and he uses minigun...
                x,y,z = getElementPosition(getLocalPlayer())
        if not createProjectile(getLocalPlayer(),19,x,y,z,200) then -- then we either create a projectile...
            outputChatBox ( "Rocket minigun overheated! Give it a rest pal!", source ) -- or if projectile limit is reached we output player a chat message
        end
    end
end

-- Don't forget to add the onClientPlayerWeaponFireFunc function as a handler for onClientPlayerWeaponFire.
addEventHandler("onClientPlayerWeaponFire", getLocalPlayer(), onClientPlayerWeaponFireFunc)
```

This example code shoots a projectile from your occupied vehicle that travels in the direction your vehicle is facing when you press vehicle\_fire (left mouse button with default controls)

``` lua

function shootProjectile()
    local vehicle = getPedOccupiedVehicle(localPlayer)
    -- Only create projectile if we are inside a vehicle
    if(vehicle)then
        local x, y, z = getElementPosition(vehicle)
        createProjectile(vehicle, 19, x, y, z)
    end
end

bindKey("vehicle_fire", "down", shootProjectile)
```

Issues
------

See also
--------

[it:createProjectile](/it:createProjectile.md "wikilink")
