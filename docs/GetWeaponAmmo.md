This function gets the total ammo a [custom weapon](/Element/Weapon.md "wikilink") has.

Syntax
------

``` lua
int getWeaponAmmo ( weapon theWeapon )
```

### Required arguments

-   **theWeapon**: The weapon to get the ammo of.

### Returns

Returns an [integer](/int.md "wikilink") containing how many ammo left has the weapon. Returns *false* if an error occured.

Example
-------

This example gets the ammo of the custom weapon and outputs it to the chatbox.

``` lua
function createCustomWeapon()
   local position = Vector3(getElementPosition(localPlayer)) -- get the localPlayer position
   local weapon = createWeapon ("m4",position.x,position.y,position.z) -- Create the weapon
     if weapon then -- If the weapon exist then
       setWeaponAmmo(weapon,5000) 
       local ammo = getWeaponAmmo(weapon)  
       outputChatBox("Total ammo: "..ammo) -- output to the chatbox
    end 
end 
addCommandHandler("weapon",createCustomWeapon)
```

Requirements
------------

See also
--------
