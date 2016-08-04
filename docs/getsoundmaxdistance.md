Gets a custom [sound](/docs/sound.md "wikilink") max distance at which the sound stops.

Syntax
------

``` lua
int getSoundMaxDistance ( element sound )
```

### Required Arguments

-   **sound:** a [sound](/docs/sound.md "wikilink") element.

### Returns

Returns an *integer* of the max distance, *false* if invalid arguments where passed.

Example
-------

<section name="Client" class="client" show="true">
``` lua
local sound = playSound3D("sounds/song.mp3", 373.14, -125.21, 1001, true)

function getmaxdistanceFunc()
  outputChatBox("Max distance: "..getSoundMaxDistance(sound))
end
addCommandHandler("getmaxdistance", getmaxdistanceFunc)
```

</section>
See Also
--------

[AR:getSoundMaxDistance](/docs/ar:getsoundmaxdistance.md "wikilink")
