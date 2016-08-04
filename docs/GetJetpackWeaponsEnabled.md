<lowercasetitle/>

This function returns all the weapons that are usable on a jetpack similar to [getJetpackWeaponEnabled](/getJetpackWeaponEnabled.md "wikilink").

Syntax
------

``` lua
 table getJetpackWeaponsEnabled() 
```

### Returns

Returns a table filled with weapon names, else an empty table.

### Code

<section name="Server" class="server" show="true">
``` lua
function getJetpackWeaponsEnabled()
    local enabled = {}
    for i=0, 46 do
        local wepName = getWeaponNameFromID(i)
        if getJetpackWeaponEnabled(wepName) then
            table.insert(enabled,wepName)
        end
    end
    return enabled
end
```

</section>
### Example

<section name="Server" class="server" show="true">
This example outputs everything in the returned table.

``` lua
addCommandHandler("weps",function()
    for _,v in ipairs(getJetpackWeaponsEnabled())do
        outputChatBox(v)
        outputConsole(v)
        outputDebugString(v)
    end
end)
```

</section>
See Also
--------
