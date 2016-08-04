This function is used to return the current pause state of the specified [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink").

Syntax
------

``` lua
bool isSoundPaused ( element theSound )
```

### Required Arguments

-   **theSound:** the [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") which pause state you want to return.

### Returns

Returns *true* if the [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") is paused, *false* if unpaused or invalid arguments were passed.

Example
-------

This example will check and see if the sound is paused or not, and tell the player.

<section name="Client" class="client" show="true">
``` lua
theSound = playSound("music/song.mp3")
function checkSongPause()
    local pause = isSoundPaused(theSound)
    if(pause == true) then
        outputChatBox("The sound is paused!")
    else
        outputChatBox("The sound is not paused!")
    end
end
addCommandHandler("checkpause", checkSongPause)
```

</section>
Changelog
---------

See Also
--------

[ar:isSoundPaused](/docs/ar:issoundpaused.md "wikilink")
