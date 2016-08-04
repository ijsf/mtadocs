This function gets all ped weapons.

Syntax
------

``` lua
table getPedWeapons ( ped thePed )
```

### Required Arguments

-   **thePed**: the ped you want to get his weapons.

### Returns

Returns a table contains the ID's of ped weapons.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getPedWeapons(ped)
    local playerWeapons = {}
    if ped and isElement(ped) and getElementType(ped) == "ped" or getElementType(ped) == "player" then
        for i=2,9 do
            local wep = getPedWeapon(ped,i)
            if wep and wep ~= 0 then
                table.insert(playerWeapons,wep)
            end
        end
    else
        return false
    end
    return playerWeapons
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example outputs all player weapons name.

``` lua
addCommandHandler("myWeapons",
    function (player)
        outputChatBox("- Your Weapons",player,255,0,0)
        for i,wep in ipairs(getPedWeapons(player)) do
            outputChatBox("You Have " .. getWeaponNameFromID(wep),player,0,255,0)
        end
    end
)
```

</section>
Author: |Mr|-Talal07-|

See Also
--------
