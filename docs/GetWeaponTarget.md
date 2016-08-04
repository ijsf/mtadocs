This functions gets the target of a [custom weapon](/docs/Element/Weapon.md "wikilink").

Syntax
------

``` lua
nil/element/float getWeaponTarget ( weapon theWeapon )
```

### Required Arguments

-   **theWeapon:** The weapon to get the target of.

### Returns

-   Returns the *target* of the [custom weapon](/docs/Element/Weapon.md "wikilink"), which can be:
    -   *[nil](/docs/nil.md "wikilink")* if the weapon is in rotation based targeting.
    -   3 [floats](/docs/float.md "wikilink") if the weapon is firing at a fixed point.
    -   an [element](/docs/element.md "wikilink") if the weapon is firing an entity.
-   Returns *false* if the weapon element is not valid.

Example
-------

This example gets the weapon target when the player hit the colshape and outputs it to the chatbox.

``` lua
local col = createColSphere(1647.33984375,1785.03125,10.671875,8) -- Create col sphere near to LV hospital
local weapon = createWeapon ("m4",1647.33984375,1785.03125,10.671875) -- Create the weapon

function onClientColShapeHit(element, matchDim )
   if (element == getLocalPlayer()) then  -- Checks whether the entering element is the local player 
     if weapon then -- if the weapon exist then
        setWeaponTarget (weapon,element,8) -- Set the weapon target to the localPlayer 
        local target = getWeaponTarget (weapon) -- get weapon target
          if target and isElement(target) and getElementType(target) == "player" then 
            outputChatBox("The target of the custom weapon: "..getPlayerName(target)) -- output to the chatbox
          end 
       end 
    end 
end
addEventHandler("onClientColShapeHit",col,onClientColShapeHit)
```

Requirements
------------

See also
--------
