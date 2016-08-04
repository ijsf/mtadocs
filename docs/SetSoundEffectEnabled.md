Used to enable or disable specific [sound](/sound.md "wikilink") effects.

Syntax
------

``` lua
bool setSoundEffectEnabled ( element sound, string effectName, bool bEnable )
```

### Required Arguments

-   **sound:** a [sound](/sound.md "wikilink") [element](/element.md "wikilink").
-   **effectName:** the effect you want to enable or disable

-   **bEnable:** *true* if you want to enable the effect, *false* if you want to disable it.

### Returns

Returns *true* if the effect was set successfully, *false* otherwise.

Example
-------

This example creates a sound and set's the flanger sound effect enabled.

``` lua
addCommandHandler("flanger",function(cmd,enabled)
    if(isElement(waterSplashes))then
        setSoundEffectEnabled(waterSplashes,cmd,enabled)
    else
        waterSplashes = playSound("splashes.mp3",true)
        setSoundEffectEnabled(waterSplashes,cmd,enabled)
    end
end,true) --set it case sensitive as we are going to get the command name and use it in the setSoundEffectEnabled
```

Changelog
---------

See Also
--------

[ar:setSoundEffectEnabled](/ar:setSoundEffectEnabled.md "wikilink")
