This function is used to change the pan level of the specified [sound](/docs/sound.md "wikilink") element.

Syntax
------

``` lua
bool setSoundPan ( element theSound, float pan )
```

### Required Arguments

-   **theSound:** The [sound](/docs/sound.md "wikilink") element which pan you want to modify.
-   **pan:** A [floating](/docs/float.md "wikilink") point number representing the desired pan level. Range is from *-1.0 (left)* to *1.0 (right)*

### Returns

Returns *true* if the [sound](/docs/sound.md "wikilink") element pan was successfully changed, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
``` lua
function playMusic ()
        local left = playSFX("genrl", 75, 6, true)    -- Play loading theme music
        local right = playSFX("genrl", 75, 7, true)
        setSoundPan(left, -1)                         -- switch the first music to left channel
        setSoundPan(right, 1)                         -- switch the second music to right channel
end

addCommandHandler("music", playMusic)                 -- add the command handler
```

</section>
See Also
--------
