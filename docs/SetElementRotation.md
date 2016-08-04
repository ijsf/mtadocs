Sets the rotation of elements according to the world (does not work with players that are on the ground).

Syntax
------

``` lua
bool setElementRotation ( element theElement, float rotX, float rotY, float rotZ [, string rotOrder = "default", bool conformPedRotation = false ] )       
```

### Required Arguments

-   **theElement:** The element whose rotation will be set
-   **rotX:** The element's rotation around the x axis in degrees
-   **rotY:** The element's rotation around the y axis in degrees
-   **rotZ:** The element's rotation around the z axis in degrees

### Optional Arguments

### Returns

Returns *true* if the element rotation was successfully set and *false* otherwise.

Example
-------

How to correctly set the rotation for a ped:

<section name="Client" class="client" show="true">
``` lua
function pedRotate ( )
    local rotX, rotY, rotZ = getElementRotation(localPlayer) -- get the local players's rotation
    setElementRotation(localPlayer,0,0,rotZ+10,"default",true) -- turn the player 10 degrees clockwise
end
addCommandHandler ( "turn", pedRotate )
```

</section>
When a player used the command “turn” and they are the driver of a vehicle the vehicle will rotate 10 degrees clockwise

<section name="Client" class="client" show="true">
``` lua
function carRotate( )
    if isPedInVehicle(localPlayer) then -- if the local client is in a vehicle
        localVehicle = getPedOccupiedVehicle(localPlayer)
        if getVehicleController(localVehicle) == localPlayer then -- if the local client is the controller (driver) of the vehicle
            local rotX, rotY, rotZ = getElementRotation(localVehicle) -- get the local client's vehicle rotation
            setElementRotation(localVehicle,rotX,rotY,rotZ+10) -- turn the vehicle 10 degrees clockwise
         end
    end
end
addCommandHandler ( "turn", carRotate )
```

</section>
Changelog
---------

See Also
--------
