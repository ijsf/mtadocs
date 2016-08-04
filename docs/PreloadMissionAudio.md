This function preloads a game sound into a specific sound slot. The sound can then be played with [PlayMissionAudio](/PlayMissionAudio.md "wikilink").

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool preloadMissionAudio ( player thePlayer, int sound, int slot )   
```

### Required Arguments

-   **thePlayer:** the [player](/player.md "wikilink") you want to play the sound for.
-   **sound:** the [int](/int.md "wikilink") sound id to play (interpreted as unsigned short). Valid values are those from the **data/AudioEvents.txt** file.
-   **slot:** [int](/int.md "wikilink") sound slot in which you preloaded the sound.

</section>
<section name="Client" class="client" show="true">
``` lua
bool preloadMissionAudio ( int sound, int slot )   
```

### Required Arguments

-   **sound:** the [int](/int.md "wikilink") sound id to play (interpreted as unsigned short). Valid values are those from the **data/AudioEvents.txt** file.
-   **slot:** [int](/int.md "wikilink") sound slot in which you preloaded the sound.

</section>
### Returns

Returns *true* if the sound was successfully preloaded, *false* otherwise.

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
