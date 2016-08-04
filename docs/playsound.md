Creates a [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") and plays it immediately after creation for the local player.
**Note:** The only supported audio formats are MP3, WAV, OGG, RIFF, MOD, XM, IT, S3M and PLS(e.g. Webstream).

Syntax
------

``` lua
 )
```

### Required Arguments

-   **soundPath:** the [filepath](/docs/filepath.md "wikilink") or URL of the sound file you want to play. (Sound specified by filepath has to be predefined in the [meta.xml](/meta.xml.md "wikilink") file with <file /> tag.)

### Optional Arguments

-   **looped:** a [boolean](/docs/boolean.md "wikilink") representing whether the sound will be looped. To loop the sound, use *true*. Loop is not available for streaming sounds, only for sound files.

### Returns

Returns a [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") if the sound was successfully created, *false* otherwise.

Example
-------

``` lua
function wasted (killer, weapon, bodypart) 
    local sound = playSound("sounds/wasted.mp3") --Play wasted.mp3 from the sounds folder
    setSoundVolume(sound, 0.5) -- set the sound volume to 50%
end

addEventHandler("onClientPlayerWasted", localPlayer, wasted) --add the event handler
```

See Also
--------

[AR:playSound](/docs/ar:playsound.md "wikilink") [DE:playSound](/DE:playSound.md "wikilink")
