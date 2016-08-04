This will tell you if a vehicle is locked.

Syntax
------

``` lua
bool isVehicleLocked ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") that you want to obtain the locked status of.

### Returns

Returns *true* if the vehicle specified is locked, *false* if is unlocked or the vehicle specified is invalid.

Example
-------

<section name="Server" class="server" show="true">
This example allows a player to lock his vehicle when he is inside it.

``` lua
function lockcar ( thePlayer )
    playervehicle = getPlayerOccupiedVehicle ( thePlayer )   -- define 'playervehicle' as the vehicle the player is in
    if ( playervehicle ) then                                -- if a player is in a vehicle
        if isVehicleLocked ( playervehicle ) then            -- and if the vehicle is already locked
            setVehicleLocked ( playervehicle, false )        -- unlock it
        else                                                 -- otherwise (if it isn't locked) 
            setVehicleLocked ( playervehicle, true )         -- lock it
        end
    end
end

function bindLockOnSpawn ( theSpawnpoint )                     -- when a player spawns
    bindKey ( source, "l", "down", "Lock car", lockcar )     -- bind the 'l' key to the 'lockcar' function
end
addEventHandler ( "onPlayerSpawn", getRootElement(), bindLockOnSpawn )     -- add an event handler for onPlayerSpawn
```

</section>
See Also
--------
