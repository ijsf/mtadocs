This function returns the maximum number of passengers that a specified vehicle can hold. Only passenger seats are counted, the driver seat is excluded.

Syntax
------

``` lua
int getVehicleMaxPassengers ( vehicle theVehicle / int modelID )
```

### Required Arguments

-   **theVehicle:** the [vehicle](/vehicle.md "wikilink") that you wish to know the maximum capacity of.

OR

-   **modelID:** the model id that you wish to know the maximum capacity of.

### Returns

Returns an [int](/int.md "wikilink") indicating the maximum number of passengers that can enter a vehicle.

Example
-------

This example creates a vehicle then gets the number of passenger seats and outputs it in the chat box.

``` lua
newcar = createVehicle ( 520, 1024, 1024, 1024 ) -- create a vehicle
numseats = getVehicleMaxPassengers ( newcar ) -- get the passenger seat count
outputChatBox ( "This vehicle supports " .. numseats .. " passengers." ) -- show it in the chat
```

See Also
--------
