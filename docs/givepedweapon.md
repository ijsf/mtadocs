Syntax
------

``` lua
 )
```

### Required Arguments

-   **thePed:** A [ped](/docs/ped.md "wikilink") element.
-   **weapon:** A whole number integer that refers to a [Weapon](/docs/weapon.md "wikilink") ID. Click [here](/Weapon.md "wikilink") for a list of possible weapon IDs.

### Optional Arguments

-   **ammo:** A whole number integer serving as the ammo amount for the given weapon. For weapons that do not require ammo, such as melee, this should be at least 1.
-   **setAsCurrent:** A boolean value determining whether or not the weapon will be set as the peds currently selected weapon.

### Returns

Returns *true* if weapon was successfully given to the ped, *false* otherwise.

Example
-------

**Example 1:** This example creates a client side ped, gives them an M4 and make them shoot once you do the command '/armedped'

``` lua
function cmdArmedPed( command )
    local x, y, z = getElementPosition(localPlayer) -- Get your position
    local thePed = createPed(0, x + 1, y, z) -- Create a CJ ped nearby
    givePedWeapon(thePed, 31, 5000, true) -- Give him 5000 rounds of M4
    setControlState(thePed, "fire", true) -- Make him shoot continuously
end
addCommandHandler("armedped", cmdArmedPed)
```

See Also
--------
