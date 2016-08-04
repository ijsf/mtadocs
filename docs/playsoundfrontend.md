This function plays a frontend sound for the specified player.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool playSoundFrontEnd ( player thePlayer, int sound )   
```

### Required Arguments

-   **thePlayer:** the [player](/docs/player.md "wikilink") you want the sound to play for.
-   **sound:** a whole [int](/docs/int.md "wikilink") specifying the sound id to play. Valid values are:

</section>
<section name="Client" class="client" show="false">
``` lua
bool playSoundFrontEnd ( int sound )   
```

### Required Arguments

-   **sound:** a whole [int](/docs/int.md "wikilink") specifying the sound id to play. Valid values are:

</section>
### Returns

Returns *true* if the sound was successfully played, *false* otherwise.

Example
-------

<section name="server" class="server" show="true">
This example plays a sound when a player spawns.

``` lua
function onPlayerSpawn ( theSpawnpoint, theTeam )
    playSoundFrontEnd ( source, 16 )
end
addEventHandler ( "onPlayerSpawn", root, onPlayerSpawn )
```

</section>
<section name="client" class="client" show="true">
This example plays a sound when the player types the command '/sound'.

``` lua
function onSoundEvent ( )
    playSoundFrontEnd ( 16 )
end
addCommandHandler("sound", onSoundEvent)
```

</section>
See Also
--------

[de:playSoundFrontEnd](/docs/de:playsoundfrontend.md "wikilink") [ar:playSoundFrontEnd](/ar:playSoundFrontEnd.md "wikilink")
