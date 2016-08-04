This function returns the current health for the specified [element](/docs/element.md "wikilink"). This can be a [player](/docs/player.md "wikilink"), a [ped](/docs/ped.md "wikilink"), or a [vehicle](/docs/vehicle.md "wikilink").

Syntax
------

``` lua
float getElementHealth ( element theElement )
```

### Required Arguments

-   **theElement:** The [player](/docs/player.md "wikilink") or [vehicle](/docs/vehicle.md "wikilink") whose health you want to check.

### Returns

Returns a float indicating the element's health, or *false* if invalid arguments were passed.

Example
-------

<section name="Clientside example" class="client" show="true">
This example outputs the health of the player who enters the command 'showhealth', and their vehicle's health.

``` lua
function showLocalHealth()
    -- get the player's health and output it
    local playerHealth = getElementHealth ( localPlayer )
    outputChatBox ( "Your health: " .. playerHealth )

    -- get the player's vehicle: if he is in one, output its health as well
    local playerVehicle = getPedOccupiedVehicle ( localPlayer )
    if playerVehicle then
        local vehicleHealth = getElementHealth ( playerVehicle ) / 10  -- Divide this by 10, as default the denominator is 1000
        outputChatBox ( "Your vehicle's health: " .. vehicleHealth )
    end
end
addCommandHandler ( "showhealth", showLocalHealth )
```

</section>
See Also
--------
