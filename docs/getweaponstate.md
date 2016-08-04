This function gets the state of a [custom weapon](/docs/element/weapon.md "wikilink").

Syntax
------

``` lua
string getWeaponState ( weapon theWeapon )
```

### Required arguments

-   **theWeapon:** the [weapon](/docs/element/weapon.md "wikilink") to get the state of.

### Returns

-   A [string](/docs/string.md "wikilink") if the [weapon](/docs/element/weapon.md "wikilink") is valid, indicating the weapon state, which can be:
    -   **reloading**: the weapon is reloading.
    -   **firing**: the weapon is constantly shooting (unless any shooting blocking flags are set) according to its assigned firing rate.
    -   **ready**: the weapon is idle.
-   *false* if an error occured or the [weapon](/docs/element/weapon.md "wikilink") is invalid.

Example
-------

This example creates a gun where the local player is and informs any player about its state.

``` lua
local function testWeaponState()
    local weapon = createWeapon("m4", getElementPosition(localPlayer)) -- Create the weapon
    outputChatBox("The weapon that has just been created state is " .. getWeaponState(weapon) .. ".") -- Tell the player its state
end
addEventHandler("onClientResourceStart", resourceRoot, testWeaponState)
```

Requirements
------------

See also
--------
