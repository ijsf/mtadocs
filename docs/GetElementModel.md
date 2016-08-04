Returns the model ID of a given element. This can be a player/ped skin, a pickup model, an object model or a vehicle model.

Syntax
------

``` lua
int getElementModel ( element theElement )
```

### Required Arguments

-   **theElement:** the element to retrieve the model ID of.

### Returns

Returns the model ID if successful, *false* otherwise.

-   For players/peds: A GTASA player model (skin) ID. See [Character Skins](/docs/Character_Skins.md "wikilink").
-   For vehicles: The [vehicle ID](/docs/Vehicle_IDs.md "wikilink") of the vehicle.
-   For objects: An [int](/docs/int.md "wikilink") specifying the model id.

Example
-------

<section class="server" name="Example 1 (Server)" show="true">
This example destroys a haystack when a player targets it.

``` lua
function onPlayerTargeted ( targetElem )
    if ( getElementType ( targetElem ) == "object" ) and ( getElementModel ( targetElem ) == 3374 ) then
        destroyElement ( targetElem )
    end
end
addEventHandler ( "onPlayerTarget", root, onPlayerTargeted )
```

</section>
<section class="server" name="Example 2 (Server)" show="true">
This example prints out a message when a Shamal or AT-400 is entered by a player.

``` lua
function planeEnter ( theVehicle, seat, jacked ) -- when someone enters a vehicle
    local id = getElementModel ( theVehicle ) -- get the model ID of the vehicle
    if id == 519 or id == 577 then -- if theVehicle is either Shamal or AT-400
        local vehicleName = getVehicleName ( theVehicle ) -- get the name of theVehicle
        outputChatBox ( "Someone stole a " .. vehicleName .. "!" ) -- announce that someone stole the plane
    end
end
-- add the event handler to the event
addEventHandler ( "onPlayerVehicleEnter", root, planeEnter )
```

</section>
See Also
--------
