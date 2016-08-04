Gets a custom [sound](/docs/sound.md "wikilink") Minimum distance at which the sound stops getting louder.

Syntax
------

``` lua
int getSoundMinDistance ( element sound )
```

### Required Arguments

-   **sound:** a [sound](/docs/sound.md "wikilink") element.

### Returns

Returns an *integer* of the minimum distance, *false* if invalid arguements where passed.

Example
-------

<section name="Client" class="client" show="true">
``` lua
local sound = playSound3D("sounds/song.mp3", 373.14, -125.21, 1001, true)

function distanceFunc()
  outputChatBox("Minimum distance: "..getSoundMinDistance(sound))
end
addCommandHandler("getdistance", distanceFunc)
```

</section>
See Also
--------

[AR:getSoundMinDistance](/docs/ar:getsoundmindistance.md "wikilink")
