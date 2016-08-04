This function can be used to set a vehicle to be locked or unlocked. Locking a vehicle restricts access to all doors of a vehicle.

Syntax
------

``` lua
bool setVehicleLocked ( vehicle theVehicle, bool locked )            
```

### Required Arguments

-   **theVehicle:** The vehicle which you wish to change the lock status of
-   **locked:** Boolean for the status you wish to set. Set *true* to lock, *false* to unlock

### Returns

Returns *true* if the operation was successful, *false* otherwise.

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
    bindKey ( source, "l", "down", lockcar )                   -- bind the 'l' key to the 'lockcar' function
end
addEventHandler ( "onPlayerSpawn", getRootElement(), bindLockOnSpawn )     -- add an event handler for onPlayerSpawn
```

</section>
See Also
--------
