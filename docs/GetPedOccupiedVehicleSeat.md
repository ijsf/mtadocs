This function gets the seat that a specific ped is sitting in in a vehicle.

Syntax
------

``` lua
int getPedOccupiedVehicleSeat ( ped thePed )
```

### Required Arguments

-   **thePed**: The [ped](/ped.md "wikilink") whose vehicle seat you're looking up.

### Returns

Returns an integer containing the number of the seat that the ped is currently in, if any. Seat 0 represents the driver's seat, any higher represents a passenger seat. Returns *false* if the ped is on foot, or the ped doesn't exist.

Example
-------

This example finds what seat a random player is sitting in and outputs it to the chat box.

``` lua
thePed = getRandomPlayer()
theVehicle = getPedOccupiedVehicle ( thePed )
if ( theVehicle ) then
    outputChatBox ( getPlayerName(thePed).." is in a vehicle in seat number " .. getPedOccupiedVehicleSeat ( thePed ) .. "." )
else
    outputChatBox ( getPlayerName(thePed).." is not in a vehicle." )
end
```

See Also
--------
