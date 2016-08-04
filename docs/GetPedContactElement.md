This function detects the element a ped is standing on. This can be a vehicle or an object.

Syntax
------

``` lua
element getPedContactElement ( ped thePed )
```

### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") of which you want to get the [element](/element.md "wikilink") he is standing on.

### Returns

Returns an [object](/docs/object.md "wikilink") or a [vehicle](/vehicle.md "wikilink") if the ped is standing on one, *false* if he is touching none or an invalid element was passed.

Example
-------

<section name="Client" class="client" show="true">
This clientside function outputs the name of the vehicle the specified player is standing on, or a message saying he isn't on one.

``` lua
function outputContactVehicleMessage ( thePlayer )
    local elementStandingOn = getPedContactElement ( thePlayer )
    if elementStandingOn and getElementType ( elementStandingOn ) == "vehicle" then
        local vehicleName = getVehicleName ( elementStandingOn )
        outputChatBox( "You're standing on a " .. vehicleName .. "." )
    else
        outputChatBox( "You're not standing on any vehicle." )
    end
end
```

</section>
See Also
--------
