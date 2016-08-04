This function is used to return the volume level of the specified [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink").

Syntax
------

``` lua
float getSoundVolume ( element theSound )
```

### Required Arguments

-   **theSound:** the [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") which volume you want to return.

### Returns

Returns a [float](/docs/float.md "wikilink") representing the volume level of the [sound](/sound.md "wikilink") [element](/element.md "wikilink"), *false* if invalid arguments were passed.

Example
-------

This example creates a sound then outputs the volume for it.

``` lua
function wasted (killer, weapon, bodypart) 
    local sound = playSound("sounds/wasted.mp3") --Play wasted.mp3 from the sounds folder
    outputChatBox("Wasted Sound volume: "..getSoundVolume(sound)) --outputs to the client the volume of the sound
end
addEventHandler("onClientPlayerWasted", getLocalPlayer(), wasted) --add the event handler
```

Changelog
---------

See Also
--------

[ar:getSoundVolume](/docs/ar:getsoundvolume.md "wikilink")
