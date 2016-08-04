This function can be used to change the playback speed of the specified [sound](/sound.md "wikilink") [element](/element.md "wikilink").

Syntax
------

``` lua
bool setSoundSpeed ( element theSound, float speed )
```

### Required Arguments

-   **theSound:** the [sound](/sound.md "wikilink") [element](/element.md "wikilink") which volume you want to modify.
-   **speed:** a [floating](/float.md "wikilink") point number representing the desired sound playback speed.

### Returns

Returns *true* if the [sound](/sound.md "wikilink") element playback speed was successfully changed, *false* otherwise.

Example
-------

``` lua
function soundFunc()
sound = playSound ( "/sounds/jizzy.mp3",true) -- Let's play a sound
setSoundSpeed ( sound, 1.2 ) -- And it will be a little bit faster !
end
addCommandHandler("play",soundFunc)
```

See Also
--------

[ar:setSoundSpeed](/ar:setSoundSpeed.md "wikilink")
