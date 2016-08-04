Syntax
------

``` lua
float getEffectDensity ( effect theEffect )
```

### Required Arguments

-   **theEffect:** The [effect](/docs/effect.md "wikilink") to get density of.

### Example

``` Lua
addCommandHandler("ses", 
function (cmd)
   local density = 4
   local x, y, z = getElementPosition (localPlayer)
   local effect = createEffect ("cement", x, y, z)
   setEffectDensity (effect, density)
   getEffectDensity (effect)
end)
```

See also
--------

[ru:getEffectDensity](/docs/ru-geteffectdensity.md "wikilink")
