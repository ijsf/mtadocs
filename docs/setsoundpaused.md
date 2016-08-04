This function is used to either pause or unpause the playback of the specified [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink").

Syntax
------

``` lua
bool setSoundPaused ( element theSound, bool paused )
```

### Required Arguments

-   **theSound:** the [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") which you want to pause/unpause.
-   **paused:** a [boolean](/docs/boolean.md "wikilink") value representing whether the sound should be paused or not. To pause the sound, use *true*.

### Returns

Returns *true* if the [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") was successfully paused, *false* otherwise.

Example
-------

This example will allow the user to toggle sounds from paused to playing, and from playing to paused

<section name="Client" class="client" show="true">
``` lua
theSound = playSound("music/song.mp3", true)
function togglePausedSound()
    if(isSoundPaused(theSound)) then --sound is paused, un-pause it
        setSoundPaused(theSound, false)
    else --sound is not paused, pause it
        setSoundPaused(theSound, true)
    end
end
addCommandHandler("pausesound", togglePausedSound)
```

</section>
Changelog
---------

See Also
--------

[AR:setSoundPaused](/docs/AR:setSoundPaused.md "wikilink")
