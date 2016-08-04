Syntax
------

``` lua
float getEffectSpeed ( effect theEffect )
```

### Required Arguments

-   **theEffect:** The [effect](/docs/effect.md "wikilink") to get the speed of.

### Returns

Returns [float](/docs/float.md "wikilink") containing the effect's speed, *false* if invalid arguments were specified.

### Example

This example adds command *ges* that creates crate explosion effect at the player's position and outputs its speed to the chatbox.

``` Lua
addCommandHandler("ges", 
function (cmd)
   local x, y, z = getElementPosition(localPlayer)
   local effect = createEffect("explosion_crate", x, y, z)
   outputChatBox("The speed: " .. tostring(getEffectSpeed(effect)))
end)
```

See also
--------

[ru:getEffectSpeed](/docs/ru:geteffectspeed.md "wikilink")
