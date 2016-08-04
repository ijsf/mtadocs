Syntax
------

``` lua
bool setEffectSpeed ( effect theEffect, float speed )
```

### Required Arguments

-   **theEffect:** The [effect](/effect.md "wikilink") to change the speed of.
-   **speed:** The speed to set.

### Returns

Returns *true* if the effect speed was succesfuly changed, *false* otherwise.

### Example

This example adds command *ses* that creates effect of a smoke at player's position and sets its speed to 5.

``` Lua
addCommandHandler("ses", 
function (cmd)
   local x, y, z = getElementPosition(localPlayer)
   local effect = createEffect("smoke30lit", x, y, z)
   setEffectSpeed(effect, 5)
end)
```

See also
--------

[ru:setEffectSpeed](/ru:setEffectSpeed.md "wikilink")
