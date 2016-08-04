This function adds an upgrade to an existing vehicle, eg: nos, hyrdraulics.

Syntax
------

``` lua
bool addVehicleUpgrade ( vehicle theVehicle, int upgrade )
```

### Required Arguments

-   **theVehicle**: The [element](/docs/element.md "wikilink") representing the [vehicle](/vehicle.md "wikilink") you wish to add the upgrade to.
-   **upgrade**: The id of the upgrade you wish to add. (1000 to 1193), *see [Vehicle Upgrades](/docs/vehicle_upgrades.md "wikilink")*

**Note:** setCameraTarget will behave strangely if you use hydraulics (upgrade id: 1087) server sided and when your camera target is the player inside the vehicle with hydraulics and if the player is not you.

Returns
-------

Returns *true* if the upgrade was successfully added to the vehicle, otherwise *false*.

Example
-------

<section name="Example 1" class="server" show="true">
This serverside function allows the user to get an upgrade by typing a command:

``` lua
-- define the handler function for our command
function consoleAddUpgrade ( thePlayer, commandName, id )
        -- make sure the player is in a vehicle
        if ( isPedInVehicle ( thePlayer ) ) then
            -- convert the given ID from a string to a number
            local id = tonumber ( id )
            -- get the player's vehicle
            local theVehicle = getPedOccupiedVehicle ( thePlayer )
            -- add the requested upgrade to the vehicle
            local success = addVehicleUpgrade ( theVehicle, id )
            -- inform the player of whether the upgrade was added successfully
            if ( success ) then
                outputConsole ( getVehicleUpgradeSlotName ( id ) .. " upgrade added.", thePlayer )
            else
                outputConsole ( "Failed to add upgrade.", thePlayer )
            end
        else
            outputConsole ( "You must be in a vehicle!", thePlayer )
        end
end
-- add the function as a handler for the "addupgrade" command
addCommandHandler ( "addupgrade", consoleAddUpgrade )
```

</section>
<section name="Example 2" class="client" show="true">
This client-side script gives vehicles a nitro upgrade whenever they pass through a certain collision shape:

``` lua
-- create a collision shape
local nitroColShape = createColSphere ( 1337, 100, 12, 2 )

-- attach the collision shape to an 'onClientColShapeHit' event
function onNitroColShapeHit ( hitElement, matchingDimension )
    if ( getElementType ( hitElement ) == "vehicle" ) then
        -- add a nitro upgrade if the element that hit the colshape is a vehicle
        addVehicleUpgrade ( hitElement, 1010 )
    end
end
addEventHandler ( "onClientColShapeHit", nitroColShape, onNitroColShapeHit )
```

</section>
See Also
--------
