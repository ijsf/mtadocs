<lowercasetitle></lowercasetitle>

This function check if sound finish.

Syntax
------

``` lua
bool isSoundFinished ( element theSound )
```

### Required Arguments

-   **theSound**: The sound element which finish state you want to return.

### Returns

Returns *true* if the [sound](/docs/sound.md "wikilink") element is finished, *false* if unfinished or invalid arguments were passed.

Code
----

<section name="Client" class="client" show="true">
``` lua
function isSoundFinished(theSound)
    return ( getSoundPosition(theSound) == getSoundLength(theSound) )
end
```

</section>
**Function created by WASSIm.**

Example
-------

This example will check and see if the sound is finished or not, and tell the player.

<section name="Client" class="client" show="true">
``` lua
addCommandHandler("checkfinish",
function ()
    local sound = playSound("music/song.mp3")
    if (isSoundFinished(sound)) then
        outputChatBox("The sound is finished!")
    else
        outputChatBox("The sound is not finished!")
    end
end)
```

</section>
See Also
--------
