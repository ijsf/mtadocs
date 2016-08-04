Syntax
------

``` lua
bool setEffectDensity ( effect theEffect, float density )
```

### Required Arguments

-   **theEffect:** The [effect](/docs/effect.md "wikilink") to change the speed of.
-   **density:** The level of density (from 0 to 2).

### Returns

Returns *true* if the density was succesfully changed, *false* otherwise.

### Example

This example adds command *sed* that creates spray effect at the player's position and sets its density to 2.

``` Lua
addCommandHandler("sed", 
function (cmd)
   local x, y, z = getElementPosition(localPlayer)
   local effect = createEffect("spraycan", x, y, z)
   setEffectDensity(effect, 2)
end)
```

See also
--------

[ru:setEffectDensity](/docs/ru:seteffectdensity.md "wikilink")
