Gets the rotation of a ped.

Syntax
------

``` lua
float getPedRotation ( ped thePed )
```

### Required Arguments

-   **thePed:** the ped to retrieve the rotation of.

### Returns

Returns the rotation of the ped, in degrees: 0 means facing north, higher values go counter clockwise. Returns *false* if an invalid element was passed.

Example
-------

<section name="Server" class="server" show="true">
This code adds a *getrot* command to get a player's current rotation.

``` lua
function outputPlayerRotation ( sourcePlayer )
    -- if the command was triggered by an ingame player
    if ( sourcePlayer ) then
        -- if he is in a vehicle
        if isPedInVehicle ( sourcePlayer ) then
            -- store the vehicle element
            local playerVehicle = getPedOccupiedVehicle ( sourcePlayer )
            -- and output its rotation
            local x,y,z = getElementRotation ( playerVehicle )
            outputChatBox ( "Your vehicle's rotation is: " .. z, sourcePlayer )
        -- if he is on foot
        else
            -- output the player's rotation
            outputChatBox ( "Your rotation is: " .. getPedRotation ( sourcePlayer ), sourcePlayer )
        end
    end
end

-- register outputPlayerRotation as a handler for the getrot command
addCommandHandler ( "getrot", outputPlayerRotation )
```

</section>
See Also
--------
