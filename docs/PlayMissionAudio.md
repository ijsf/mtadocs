This function plays a game sound in a specific slot. Be sure to preload your sound with [PreloadMissionAudio](/PreloadMissionAudio.md "wikilink") into the slot beforehand. An optional position element can be specified.

Usage
-----

Both server side and client side. “thePlayer” argument isn't used in the client side version of this function.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool playMissionAudio ( player thePlayer, int slot, float x, float y, float z )
```

### Required Arguments

-   **thePlayer**: the [player](/player.md "wikilink") you want to play the sound for.
-   **slot**: [int](/int.md "wikilink") sound slot in which you preloaded the sound
-   **x**: [float](/float.md "wikilink") position's x coordinate
-   **y**: [float](/float.md "wikilink") position's y coordinate
-   **z**: [float](/float.md "wikilink") position's z coordinate

</section>
<section name="Client" class="client" show="false">
``` lua
bool playMissionAudio ( int slot, float x, float y, float z )
```

### Required Arguments

-   **thePlayer**: the [player](/player.md "wikilink") you want to play the sound for.
-   **slot**: [int](/int.md "wikilink") sound slot in which you preloaded the sound
-   **x**: [float](/float.md "wikilink") position's x coordinate
-   **y**: [float](/float.md "wikilink") position's y coordinate
-   **z**: [float](/float.md "wikilink") position's z coordinate

</section>
### Returns

Returns *true* if the sound was successfully played, *false* otherwise.

Example
-------

<section name="server" class="server" show="true">
This example plays a sound when a player spawns

``` lua
function onPlayerSpawn ( theSpawnpoint, theTeam )
    preloadMissionAudio ( source, 5000, 1 )
    local x, y, z = getElementPosition ( source )
    playMissionAudio ( source, 1, x, y, z )
end
addEventHandler ( "onPlayerSpawn", getElementRoot(), onPlayerSpawn )
```

</section>
<section name="client" class="client" show="true">
This example plays a sound when the server triggers the onSoundEvent client event.

``` lua
function onSoundEvent ( )
    preloadMissionAudio ( source, 5000, 1 )
    local x, y, z = getElementPosition ( source )
    playMissionAudio ( 1, x, y, z )
end
addEvent ( "onSoundEvent" )
addEventHandler ( "onSoundEvent", getElementRoot(), onSoundEvent )
```

</section>
See Also
--------
