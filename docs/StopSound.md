Stops the sound playback for specified [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink"). The sound element is also destroyed.

Syntax
------

``` lua
bool stopSound ( element theSound )
```

### Required Arguments

-   **theSound:** the [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") you want to stop playing.

### Returns

Returns *true* if the sound was successfully stopped, *false* otherwise.

Example
-------

``` lua
function startMySound()
    sound = playSound( "sound.mp3", true )
end
addEventHandler( "onClientResourceStart", resourceRoot, startMySound )

function stopMySound()
    stopSound( sound )
end
addCommandHandler ( "stopsound", stopMySound ) --using the command 'stopsound' will stop the sound
```

See Also
--------

[AR:stopSound](/docs/AR:stopSound.md "wikilink")
