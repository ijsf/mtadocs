This function returns the speed of an element in m/s, km/h or mph.

Syntax
------

``` lua
float/nil getElementSpeed ( element theElement [, int/string unit="m/s" ] )
```

### Required arguments

-   **theElement**: the [element](/docs/element.md "wikilink") you want to get the speed of. Compatible [element](/element.md "wikilink") types are:
    -   [Players](/docs/Player.md "wikilink").
    -   [Peds](/docs/Ped.md "wikilink").
    -   [Objects](/docs/Object.md "wikilink").
    -   [Vehicles](/docs/Vehicle.md "wikilink").

### Optional arguments

-   **unit**: the unit of the speed returned. If not specified, the unit will be *m/s*. It can be specified as a *[string](/docs/string.md "wikilink")* or *number* as follows:
    -   **0** or **m/s**: meters per second (speed unit of the [International System of Units](http://en.wikipedia.org/wiki/International_System_of_Units), used in formal contexts).
    -   **1** or **km/h**: kilometres per hour (the most common speed unit, used in most countries).
    -   **2** or **mph**: miles per hour (used in some English-speaking countries).

Returns
-------

This function returns a *number* containing the [element](/docs/element.md "wikilink")'s speed if the arguments provided are valid. It returns *[nil](/nil.md "wikilink")* plus an *error* otherwise.

Code
----

<section name="Function source" class="both" show="true">
**This function requires MTA: SA 1.4** or higher to work. It doesn't need, however, to activate *OOP*.

``` lua
function getElementSpeed(theElement, unit)
    -- Check arguments for errors
    assert(isElement(theElement), "Bad argument 1 @ getElementSpeed (element expected, got " .. type(theElement) .. ")")
    assert(getElementType(theElement) == "player" or getElementType(theElement) == "ped" or getElementType(theElement) == "object" or getElementType(theElement) == "vehicle", "Invalid element type @ getElementSpeed (player/ped/object/vehicle expected, got " .. getElementType(theElement) .. ")")
    assert((unit == nil or type(unit) == "string" or type(unit) == "number") and (unit == nil or (tonumber(unit) and (tonumber(unit) == 0 or tonumber(unit) == 1 or tonumber(unit) == 2)) or unit == "m/s" or unit == "km/h" or unit == "mph"), "Bad argument 2 @ getElementSpeed (invalid speed unit)")
    -- Default to m/s if no unit specified and 'ignore' argument type if the string contains a number
    unit = unit == nil and 0 or ((not tonumber(unit)) and unit or tonumber(unit))
    -- Setup our multiplier to convert the velocity to the specified unit
    local mult = (unit == 0 or unit == "m/s") and 50 or ((unit == 1 or unit == "km/h") and 180 or 111.84681456)
    -- Return the speed by calculating the length of the velocity vector, after converting the velocity to the specified unit
    return (Vector3(getElementVelocity(theElement)) * mult).length
end
```

</section>
Example
-------

<section name="Clientside example" class="client" show="true">
This example draws the local player's speed rounded to a single decimal in the up-right corner of the screen in different units.

``` lua
local sx = guiGetScreenSize()
local function drawSpeed()
    local speedms, speedkmh, speedmph = getElementSpeed(localPlayer), getElementSpeed(localPlayer, 1), getElementSpeed(localPlayer, 2)
    local roundedSpeedms, roundedSpeedkmh, roundedSpeedmph = math.floor(speedms) == speedms and speedms or string.format(speedms, "%.1f"), math.floor(speedkmh) == speedkmh and speedkmh or string.format(speedkmh, "%.1f"), math.floor(speedmph) == speedmph and speedmph or string.format(speedmph, "%.1f")
    local speedoText = "Current speed: " .. roundedSpeedms .. " m/s | " .. roundedSpeedkmh .. " km/h | " .. roundedSpeedmph .. " mph"
    dxDrawText(speedoText, sx - dxGetTextWidth(speedoText), 0)
end
addEventHandler("onClientPreRender", root, drawSpeed)
```

</section>
See also
--------
