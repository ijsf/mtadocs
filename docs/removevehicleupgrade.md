Description
-----------

This function removes an already existing upgrade from the specified vehicle, eg: nos, hydraulics. Defined in San Andreas\\data\\maps\\veh\_mods\\veh\_mods.ide.

Syntax
------

``` lua
bool removeVehicleUpgrade ( vehicle theVehicle, int upgrade )
```

### Required Arguments

-   **theVehicle**: The [element](/docs/element.md "wikilink") representing the [vehicle](/vehicle.md "wikilink") you wish to remove the upgrade from
-   **upgrade**: The ID of the upgrade you wish to remove.

Returns
-------

Returns *true* if the upgrade was successfully removed from the vehicle, otherwise *false*.

Example
-------

<section name="Server" class="server" show="true">
This script defines a 'nos' console command that adds a NOS upgrade to the vehicle that the player who executes the command is sitting in. It also adds a 'removenos' command which allows removal of a player's nos.

``` lua
function addNOS ( sourcePlayer, command )
    theVehicle = getPlayerOccupiedVehicle ( sourcePlayer )
    if ( theVehicle ) then
        addVehicleUpgrade ( theVehicle, 1010 )     -- NOS 10x
    end
end
addCommandHandler ( "nos", addNOS )

function remNOS ( sourcePlayer, command )
    theVehicle = getPlayerOccupiedVehicle ( sourcePlayer )
    if ( theVehicle ) then
        removeVehicleUpgrade ( theVehicle, 1010 )
    end
end
addCommandHandler ( "removenos", remNOS )
```

</section>
<section name="Client" class="client" show="false">
This script defines a 'nos' console command that adds a NOS upgrade to the vehicle that the player who executes the command is sitting in. It also adds a 'removenos' command which allows removal of a player's nos. This example is clientside and may cause desync.

``` lua
function addNOS ( command )
    theVehicle = getPlayerOccupiedVehicle ( getLocalPlayer() )
    if ( theVehicle ) then
        addVehicleUpgrade ( theVehicle, 1010 )     -- NOS 10x
    end
end
addCommandHandler ( "nos", addNOS )

function remNOS ( command )
    theVehicle = getPlayerOccupiedVehicle ( getLocalPlayer() )
    if ( theVehicle ) then
        removeVehicleUpgrade ( theVehicle, 1010 )
    end
end
addCommandHandler ( "removenos", remNOS )
```

</section>
See Also
--------
