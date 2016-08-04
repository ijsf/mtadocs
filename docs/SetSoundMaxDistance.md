Sets a custom [sound](/sound.md "wikilink") max distance at which the sound stops.

Syntax
------

``` lua
bool setSoundMaxDistance ( element sound, int distance )
```

### Required Arguments

-   **sound:** a [sound](/sound.md "wikilink") element.
-   **distance:** the default value for this is 20

### Returns

Returns a *true* if the max distance was set, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
``` lua
local sound = playSound3D("sounds/song.mp3", 373.14, -125.21, 1001, true)

function maxdistanceFunc(command, param)
  setSoundMaxDistance(sound, tonumber(param))
end
addCommandHandler("setmaxdistance", maxdistanceFunc)
```

</section>
See Also
--------

[ar:setSoundMaxDistance](/ar:setSoundMaxDistance.md "wikilink")
