This function is used to return the playback speed of the specified [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink").

Syntax
------

``` lua
float getSoundSpeed ( element theSound )
```

### Required Arguments

-   **theSound:** the [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") which playback speed you want to return.

### Returns

Returns an [float](/docs/float.md "wikilink") value indicating the playback speed of the [sound](/sound.md "wikilink") [element](/element.md "wikilink"). Default sound playback speed is **1.0**.

Example
-------

<section name="Client" class="client" show="true">
``` lua
function outputSpeed(soundname) 
    local sound = playSound("sounds/"..tostring(soundname)..".mp3") --Play the sound from the sounds folder
    setSoundVolume(sound, 0.5) -- set the sound volume to 50%
    outputChatBox("The sound speed : "..getSoundSpeed(sound)) -- output the sound speed
end
addCommandHandler("soundspeed",outputSpeed)
```

</section>
See Also
--------

[ar:getSoundSpeed](/docs/ar:getSoundSpeed.md "wikilink")
