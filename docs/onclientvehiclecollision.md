This event is triggered when a vehicle collides with an [element](/docs/element.md "wikilink") or a world object.

Note that the collision reported by this event doesn't always damage the vehicle by default (this event triggers when hitting lamp posts, but the vehicle isn't damaged by them automatically, for example). If you want to deal with real damage, please refer to [onClientVehicleDamage](/docs/onclientvehicledamage.md "wikilink").

Parameters
----------

``` lua
element theHitElement, float force, int bodypart, float collisionX, float collisionY, float collisionZ, float normalX, float normalY, float normalZ, float hitElementForce, int model
```

**Note:** *theHitElement* will be nil or false if it's a default SA object and it will trigger twice for vehicles because one vehicle hit another and one got hit by another.

-   **theHitElement:** the other entity, or nil if the vehicle collided with the world
-   **force:** the impact magnitude (Note: this is NOT the damage it is a force value which is then multiplied by the vehicles collision damage multiplier. for an example of this see below)
-   **bodyPart:** the bodypart that hit the other element
-   **collisionX/Y/Z:** the position the collision took place
-   **normalX/Y/Z:** the surface normal of the hit object
-   **hitElementforce:** 0 for non vehicles or the force of the other vehicle
-   **model:** model of the hit element (useful to detect building collisions as hitElement will be nil)

Type
----

This event is a pre reaction event meaning it occurs before any game level reaction to the collision which include:

-   Bike knock off effect
-   Collision particles
-   All types of damage reaction such as broken wings, wind shields, engine damage, broken lights and so on
-   Audio of the impact

Source
------

The source of this event is the vehicle that collided with something.

Issues
------

Example
-------

``` lua
addEventHandler("onClientVehicleCollision", root,
    function(collider,force, bodyPart, x, y, z, nx, ny, nz)
         if ( source == getPedOccupiedVehicle(localPlayer) ) then
             -- force does not take into account the collision damage multiplier (this is what makes heavy vehicles take less damage than banshees for instance) so take that into account to get the damage dealt
             local fDamageMultiplier = getVehicleHandling(source).collisionDamageMultiplier
             -- Create a marker (Scaled down to 1% of the actual damage otherwise we will get huge markers)
             local m = createMarker(x, y, z, "corona", force * fDamageMultiplier * 0.01, 0, 9, 231)
             -- Destroy the marker in 2 seconds
             setTimer(destroyElement, 2000, 1, m)
         end
    end
)
```

``` lua
-- This code works because onClientVehicleCollision is triggered before any SA reaction to the collision, therefore we can update the knocked off bike status just before the collision and stop the falling off effect happening :)
addEventHandler("onClientVehicleCollision", root,
    function ( hit ) 
        -- firstly did we trigger this event
        if ( source == getPedOccupiedVehicle(localPlayer) ) then
            -- knock off defaults to false
            local knockOff = false 
            -- if our hit element is nil (we just hit an SA map object)
            if ( hit == nil ) then 
                -- set knockOff to true 
                knockOff = true 
            end 
  
            -- update our can be knocked off bike status accordingly
            setPedCanBeKnockedOffBike(localPlayer, knockOff) 
        end
    end
)
```

See Also
--------

### Client vehicle events

### Client event functions
