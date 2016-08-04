Syntax
------

``` lua
bool setSoundProperties(element sound, float fSampleRate, float fTempo, float fPitch, bool bReverse )
```

### Required Arguments

-   **sound:** a [sound](/docs/sound.md "wikilink") [element](/docs/element.md "wikilink") that is created using [playSound](/docs/playsound.md "wikilink") or [playSound3D](/docs/playsound3d.md "wikilink")

<!-- -->

-   **fSampleRate:** a [float](/docs/float.md "wikilink") that defines the new sound's [sample rate](http://en.wikipedia.org/wiki/Sampling_rate)

<!-- -->

-   **fTempo:** a [float](/docs/float.md "wikilink") that defines the new sound [tempo](http://en.wikipedia.org/wiki/Tempo)

<!-- -->

-   **fPitch:** a [float](/docs/float.md "wikilink") that defines the new sound [pitch](http://en.wikipedia.org/wiki/Pitch_%28music%29)

<!-- -->

-   **bReverse:** a [boolean](/docs/boolean.md "wikilink") representing whether the sound will be reversed or not.

### Returns

Returns *true* if the properties sucessfully set, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
``` lua
function editSongSound()
    local sound = playSound("song.wav", false) -- Play the file 'song.wav' and make it play only once
    setSoundProperties(sound, 48000.0, 128.00, 440.0, false) -- Set its samplerate to 48,000 Hz, tempo to 128.00, pitch to 440 Hz and not reversed
end
addEventHandler("onClientResourceStart", resourceRoot, editSongSound) -- Execute the function when the resource is started
```

</section>
See Also
--------

[ar:setSoundProperties](/docs/ar:setsoundproperties.md "wikilink")
