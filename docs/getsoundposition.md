This function is used to return the current seek position of the specified [sound](/docs/sound.md "wikilink") element. If the element is a player, this function will use the players voice.

Syntax
------

``` lua
float getSoundPosition ( element theSound )
```

### Required Arguments

-   **theSound:** The [sound](/docs/sound.md "wikilink") element which seek position you want to return.

### Returns

Returns a [float](/docs/float.md "wikilink") value indicating the seek position of the [sound](/docs/sound.md "wikilink") element in seconds.

Example
-------

Plays a sound then outputs the seek position.

``` lua
local sound = playSound("randomSound.mp3",false) --Play a sound
local soundPosition = getSoundPosition(sound) --Get the current sound position
outputChatBox("The current seek position of the sound is: " .. soundPosition .. ".")
```

Changelog
---------

See Also
--------

[AR:getSoundPosition](/docs/ar:getsoundposition.md "wikilink")
