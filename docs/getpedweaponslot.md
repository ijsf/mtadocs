This function gets a ped's selected weapon slot.

Syntax
------

``` lua
int getPedWeaponSlot ( ped thePed )
```

### Required Arguments

-   **thePed:** the ped to get the current weapon slot of.

### Returns

Returns the selected weapon slot ID on success, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
``` lua
function doesPlayerHaveWeapon(source)
    local pedSlot = getPedWeaponSlot ( source )
    if (pedSlot == 0)   then
        outputChatBox("Your weapon is not in your hands ;)", source)
    end
end
addCommandHandler("weapon", doesPlayerHaveWeapon)
```

</section>
See Also
--------
