Syntax
------

``` lua
float, float, float, bool getSoundProperties( element sound )
```

### Required Arguments

-   **sound:** a [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") that is created using [playSound](/playSound.md "wikilink") or [playSound3D](/playSound3D.md "wikilink")

### Returns

This function returns 3 [floats](/docs/float.md "wikilink") and a [boolean](/boolean.md "wikilink") value:

The first float is the sound's [sample rate](http://en.wikipedia.org/wiki/Sampling_rate), the second one the sound's [tempo](http://en.wikipedia.org/wiki/Tempo), and the third one the [pitch](http://en.wikipedia.org/wiki/Pitch_%28music%29) of the sound. The boolean representing whether the sound is reversed or not.

Example
-------

**Example 1:** This example would return three float values representing the sample rate, tempo, pitch and a boolean value representing whether the sound is reversed or not, every 5 seconds.

``` lua
local sound 
local timer

addCommandHandler("playsound",
function () 
    sound = playSound("wasted.mp3")
    timer = setTimer(function() soundProperties(sound) end, 5000, 0)
end
)

function soundProperties(sound)
    local sampleRate, tempo, pitch, isReversed = getSoundProperties(sound) --gets the sample rate, tempo, pitch and a boolean value representing whether the sound is reversed or not.
    outputChatBox(sampleRate.." "..tempo.." "..pitch.." "..tostring(isReversed))
end
```

See Also
--------

[ar:getSoundProperties](/docs/ar:getSoundProperties.md "wikilink")
