Sets a custom [sound](/docs/sound.md "wikilink") Minimum distance at which the sound stops getting louder.

Syntax
------

``` lua
bool setSoundMinDistance ( element sound, int distance )
```

### Required Arguments

-   **sound:** a [sound](/docs/sound.md "wikilink") element.
-   **distance:** an integer representing the distance the sound stops getting louder. the default value for this is 5

### Returns

Returns a *true* if the minimum distance was set, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
``` lua
local sound = playSound3D("sounds/song.mp3", 373.14, -125.21, 1001, true)

function distanceFunc(command, param)
  setSoundMinDistance(sound, tonumber(param))
end
addCommandHandler("setdistance", distanceFunc)
```

</section>
See Also
--------

[AR:setSoundMinDistance](/docs/ar:setsoundmindistance.md "wikilink")
