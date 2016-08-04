This function gets the seat that a specific player is sitting in in a vehicle.

Syntax
------

``` lua
int getPlayerOccupiedVehicleSeat ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/docs/player.md "wikilink") whose vehicle seat you're looking up.

### Returns

Returns an integer containing the number of the seat that the player is currently in, if any. Returns *false* if the player is on foot, or the player doesn't exist.

Example
-------

This example finds what seat the player called 'someguy' is sitting in and outputs it to the chat box.

``` lua
thePlayer = getPlayerFromNick ( "someguy" )
theVehicle = getPlayerOccupiedVehicle ( thePlayer )
if ( theVehicle ) then
    outputChatBox ( "someguy is in a vehicle in seat number " .. getPlayerOccupiedVehicleSeat ( thePlayer ) .. "." )
else
    outputChatBox ( "someguy is not in a vehicle." )
end
```

See Also
--------
