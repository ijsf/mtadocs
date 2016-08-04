This function is used to change the volume level of the specified [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink"). Use a player element to control a players voice with this function.

Syntax
------

``` lua
bool setSoundVolume ( element theSound, float volume )
```

### Required Arguments

-   **theSound:** The [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") which volume you want to modify.
-   **volume:** A [floating](/docs/float.md "wikilink") point number representing the desired volume level. Range is from **0.0** to **1.0**

### Returns

Returns *true* if the [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") volume was successfully changed, *false* otherwise.

Example
-------

``` lua
function wasted (killer, weapon, bodypart)
        local sound = playSound("sounds/wasted.mp3") --Play wasted.mp3 from the sounds folder
        setSoundVolume(sound, 0.5) -- set the sound volume to 50%
end

addEventHandler("onClientPlayerWasted", localPlayer, wasted) --add the event handler 
```

Changelog
---------

See Also
--------

[AR:setSoundVolume](/docs/ar:setsoundvolume.md "wikilink")
