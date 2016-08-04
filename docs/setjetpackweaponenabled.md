This function sets a weapon usable while using the Jetpack.

Syntax
------

``` lua
bool setJetpackWeaponEnabled(string weapon, bool enabled)
```

### Required Arguments

-   **weapon** The weapon that's being set usable on a Jetpack. Names can be: (Case is ignored)

-   **enabled** A bool representing whether the weapon is enabled or disabled.

### Returns

Returns true, else false if invalid arguments are passed.

Example
-------

    addEventHandler("onResourceStart",resourceRoot,function()
         if setJetpackWeaponEnabled("31",true) then
              outputChatBox(getWeaponNameFromID(31).." is now enabled for jetpacks!")
         end
    end)

Issues
------

Requirements
------------

See Also
--------
