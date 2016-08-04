This function will set the color of a vehicle. Colors are in RGB format, vehicles can have up to 4 colors. Most vehicles have 2 colors only.

### Returns

Returns *true* if vehicle's color was set, *false* if an invalid vehicle or invalid colors were specified.

Example
-------

<section name="Example 1" class="server" show="true">
This example implements a serverside *random\_color* console command.

``` lua
addCommandHandler( 'random_color',
    function( uPlayer )
        if isPedInVehicle( uPlayer ) then
            local uVehicle = getPedOccupiedVehicle( uPlayer )
            if uVehicle then
                local r, g, b = math.random( 255 ), math.random( 255 ), math.random( 255 )
                setVehicleColor( uVehicle, r, g, b )
            end
        end
    end
)
```

</section>
Issues
------

See Also
--------
