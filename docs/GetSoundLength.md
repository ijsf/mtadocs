This function is used to return the playback length of the specified [sound](/sound.md "wikilink") element.

Syntax
------

``` lua
float getSoundLength ( element theSound )
```

### Required Arguments

-   **theSound:** the [sound](/sound.md "wikilink") element which length you want to return.

### Returns

Returns an [float](/float.md "wikilink") value indicating the playback length of the [sound](/sound.md "wikilink") element in seconds.

Example
-------

Plays a sound then outputs the sound length.

``` lua
local sound = playSound("money.mp3",false) --Play a sound
local soundLength = getSoundLength(sound) --Get the length of the sound
outputChatBox("This sound is :" ..soundLength.. " long!")
```

Changelog
---------

See Also
--------

[ar:getSoundLength](/ar:getSoundLength.md "wikilink")
