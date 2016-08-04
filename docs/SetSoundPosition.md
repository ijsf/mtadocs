This function is used to change the seek position of the specified [sound](/sound.md "wikilink") element. Use a player element to control a players voice with this function.

Syntax
------

``` lua
bool setSoundPosition ( element theSound, float pos )
```

### Required Arguments

-   **theSound:** the [sound](/sound.md "wikilink") element which seek position you want to modify.
-   **pos:** an float value representing the new seek position of the sound. Integer part of this value - seconds, fractional part - milliseconds.

### Returns

Returns *true* if the [sound](/sound.md "wikilink") element's seek position was successfully changed, *false* otherwise.

Example
-------

This example allows the player to set how many milliseconds into the song he wants it to play from

``` lua
theSound = playSound("music/song.mp3")
function setSongPos(cmd, tm)
    tm = tonumber(tm)
    local ssp = setSoundPosition(theSound,tm)
    if ssp then
        outputChatBox("Sound is now playing from: "..tostring(tm))
    else
        outputChatBox("An error has occured.")
    end
end
addCommandHandler("skipsong", setSongPos)
```

Changelog
---------

See Also
--------

[ar:setSoundPosition](/ar:setSoundPosition.md "wikilink")
