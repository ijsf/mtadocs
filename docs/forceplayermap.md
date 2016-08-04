This function is used to forcefully show a player's radar map.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool forcePlayerMap ( player thePlayer, bool forceOn )
```

### Required Arguments

-   **thePlayer**: A [player](/docs/player.md "wikilink") object referencing the specified player
-   **forceOn**: A boolean value representing whether or not the players radar map will be forced on

</section>
<section name="Client" class="client" show="true">
``` lua
bool forcePlayerMap ( bool forceOn )
```

### Required Arguments

-   **forceOn**: A boolean value representing whether or not the players radar map will be forced on

</section>
### Returns

Returns *true* if the player's radar map was forced on, *false* otherwise.

Example
-------

This example forces the radar map to show for the player named “dave” on for 10 seconds, if it hasn't been already.

``` lua
-- Get the player named "dave"
dave = getPlayerFromName ( "dave" )
-- Make sure we found him
if ( dave ) then
    if not isPlayerMapForced ( dave ) then                  -- if his radar map isn't already forced on
        forcePlayerMap ( dave, true )                       -- force it on
        setTimer ( forcePlayerMap, 10000, 1, dave, false )  -- stop forcing in 10 seconds
    end
end
```

See Also
--------

[ru:forcePlayerMap](/docs/ru-forceplayermap.md "wikilink")
