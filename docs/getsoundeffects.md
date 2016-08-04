Returns the states of all effects of a sound.

Syntax
------

``` lua
table getSoundEffects ( element sound )
```

### Required Arguments

-   **sound:** a [sound](/docs/sound.md "wikilink") element.

### Returns

Returns a [table](/docs/table.md "wikilink") with the effect names as the keys, and their states as the values if successful. Otherwise, it returns *false*.

**Sound effect names:**

Example
-------

``` lua
function switchEffects(sound)
    for _,v in ipairs(getSoundEffects(sound)) do -- Go through the whole list of sound effects for the sound
        if v == "gargle" then -- If the sound effect is 'gargle', proceed
            setSoundEffectEnabled(sound, "gargle", false) -- Disable the 'gargle' -effect
        end
    end
end
```

See Also
--------

[ar:getSoundEffects](/docs/ar-getsoundeffects.md "wikilink") [de:getSoundEffects](/docs/de-getsoundeffects.md "wikilink")
