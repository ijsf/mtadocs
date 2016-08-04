This function allows you to determine whether a vehicle is blown or still intact.

Syntax
------

``` lua
bool isVehicleBlown ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/vehicle.md "wikilink") that you want to obtain the blown status of.

### Returns

Returns *true* if the vehicle specified has blown up, *false* if it is still intact or the vehicle specified is invalid.

Example
-------

<section name="Server" class="server" show="true">
This example creates a taxi and checks whether the taxi has blown up or not every time somebody types "/taxi".

``` lua
theTaxi = createVehicle ( 420, 1, 1, 17 ) -- Add a taxi in the middle of SA

function checkTaxi ( thePlayer, command )
    if ( isVehicleBlown ( theTaxi ) ) then -- Check whether it's blown or not
        outputChatBox ( "The taxi has blown up.", thePlayer, 255, 0, 0 ) -- If so, we'll output it
    else -- Anything else (if it's not)
        outputChatBox ( "The taxi has not blown.", thePlayer, 255, 0, 0 ) -- If not, we'll output that instead
    end
end
addCommandHandler ( "taxi", checkTaxi ) -- Make it check when somebody types "/taxi"
```

</section>
See Also
--------
