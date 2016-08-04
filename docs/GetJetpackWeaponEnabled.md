This function checks if a weapon is usable while on a Jetpack.

Syntax
------

``` lua
bool getJetpackWeaponEnabled(string weapon)
```

### Required Arguments

-   **weapon:** The weapon that's being checked if it's usable on a Jetpack.

### Returns

Returns true if the weapon is enabled, else false if the weapon isn't or invalid arguments are passed.

Example
-------

    addCommandHandler("isJPEnabled",function(ped,_,wep)
        if ped then
            outputChatBox(tostring(getJetpackWeaponEnabled(wep)),ped)
        end
    end)

Requirements
------------

See Also
--------
