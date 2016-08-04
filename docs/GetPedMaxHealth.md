<lowercasetitle></lowercasetitle>

This functions gets the maximum health a [ped](/ped.md "wikilink") should have, considering its max health (24) [stat](/Template:Stats.md "wikilink").

Syntax
------

``` lua
float getPedMaxHealth ( ped thePed )
```

### Required Arguments

-   **thePed:** the [ped](/ped.md "wikilink") whose maximum health you want to get.

### Returns

A *float* with the maximum health of the specified [ped](/ped.md "wikilink"), an error if a invalid [ped](/ped.md "wikilink") was passed.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getPedMaxHealth(ped)
    -- Output an error and stop executing the function if the argument is not valid
    assert(isElement(ped) and (getElementType(ped) == "ped" or getElementType(ped) == "player"), "Bad argument @ 'getPedMaxHealth' [Expected ped/player at argument 1, got " .. tostring(ped) .. "]")

    -- Grab his player health stat.
    local stat = getPedStat(ped, 24)

    -- Do a linear interpolation to get how many health a ped can have.
    -- Assumes: 100 health = 569 stat, 200 health = 1000 stat.
    local maxhealth = 100 + (stat - 569) / 4.31

    -- Return the max health. Make sure it can't be below 1
    return math.max(1, maxhealth)
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
The next code snippet adds a /healme command, which always entirely heals the player who types it.

``` lua
function healCommand(player)
    if getElementHealth(player) < getPedMaxHealth(player) then
        setElementHealth(player, getPedMaxHealth(player))
        outputChatBox("You have just got healed!", player, 0, 255, 0)
    else
        outputChatBox("Your health is already full.", player, 255, 0, 0)
    end
end
addCommandHandler("healme", healCommand)
```

</section>
See also
--------
