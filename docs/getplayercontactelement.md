This function detects the element a player is standing on. This can be a vehicle or an object. Note that the server is unable to retrieve contact elements that are created clientside.

Syntax
------

``` lua
element getPlayerContactElement ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") you want to get the [element](/docs/element.md "wikilink") he is touching from.

### Returns

Returns an [object](/docs/object.md "wikilink") or a [vehicle](/docs/vehicle.md "wikilink") if the player is standing on one, *false* if he is touching none or is a invalid player.

Example
-------

This clientside function outputs the name of the vehicle the specified player is standing on, or a message saying he isn't on one.

``` lua
function outputContactVehicleMessage ( thePlayer )
  local elementStandingOn = getPlayerContactElement( thePlayer )
  if getElementType( elementStandingOn ) == "vehicle" then
    local vehicleName = getVehicleName( elementStandingOn )
    outputChatBox( "The player is standing on a " .. vehicleName .. "." )
  else
    outputChatBox( "The player isn't standing on any vehicle." )
  end
end
```

See Also
--------
