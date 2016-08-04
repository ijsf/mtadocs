This function is used to get the pan level of the specified [sound](/docs/sound.md "wikilink") element.

Syntax
------

``` lua
float getSoundPan ( element theSound )
```

### Required Arguments

-   **theSound:** the [sound](/docs/sound.md "wikilink") element which pan you want to get.

### Returns

Returns *float* value with range from *-1.0 (left)* to *1.0 (right)*, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
``` lua
function playMusic ()
        local song = playSound('song.mp3')
        setSoundPan(song, 0.3)
        outputChatBox("Current pan is "..tostring(getSoundPan(song)))
end

addCommandHandler("music", playMusic)
```

</section>
See Also
--------
