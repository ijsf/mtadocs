<lowercasetitle></lowercasetitle>

This functions gets the maximum oxigen level a [ped](/docs/ped.md "wikilink") should have, considering its max underwater stamina (225) [stat](/Template:Stats.md "wikilink").

Syntax
------

``` lua
float getPedMaxOxygenLevel ( ped thePed )
```

### Required Arguments

-   **thePed:** the [ped](/docs/ped.md "wikilink") whose maximum oxygen level you want to get.

### Returns

A *float* with the maximum oxygen level of the specified [ped](/docs/ped.md "wikilink"), an error if a invalid [ped](/ped.md "wikilink") was passed.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getPedMaxOxygenLevel(ped)
    -- Output an error and stop executing the function if the argument is not valid
    assert(isElement(ped) and (getElementType(ped) == "ped" or getElementType(ped) == "player"), "Bad argument @ 'getPedMaxOxygenLevel' [Expected ped at argument 1, got " .. tostring(ped) .. "]")

    -- Grab his ped underwater stamina stat.
    local stat = getPedStat(ped, 225)

    -- Do a linear interpolation to get how many oxygen a ped can have.
    -- Assumes: 1750 level = 0 stat, 3250 level = 1000 stat.
    local maxoxygen = 1750 + stat * 1.5

    -- Return the max oxygen level.
    return maxoxygen
end
```

</section>
Example
-------

<section name="Client side" class="client" show="true">
The next code snippet adds a /breathe command, which always fills the lungs player who types it.

``` lua
function breathCommand()
    if getPedOxygenLevel(localPlayer) < getPedMaxOxygenLevel(localPlayer) then
        setPedOxygenLevel(localPlayer, getPedMaxOxygenLevel(localPlayer))
        outputChatBox("You have just breathed a lungful!", 128, 192, 255)
    else
        outputChatBox("Your lungs are already full.", 255, 0, 0)
    end
end
addCommandHandler("breathe", breathCommand)
```

</section>
See also
--------
