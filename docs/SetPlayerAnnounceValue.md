This function allows you to change ASE announce values for any player using a specified key. As an example this can be used to change the “score” value which will be shown at [game-monitor.com](http://www.game-monitor.com)'s server list.

Syntax
------

``` lua
bool setPlayerAnnounceValue ( element thePlayer, string key, string value )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") whos announce value you wish to change.
-   **key:** The key which the value will be stored at.
-   **value:** The value you wish to store.

### Returns

Returns *true* if the value was set succesfully, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This small example adds a command that allows you to set your own “score” value.

``` lua
function setScore ( playerSource, cmdName, scoreValue )
    if ( scoreValue ) then
        setPlayerAnnounceValue ( playerSource, "score", scoreValue )
    end
end

addCommandHandler ( "score", setScore )
```

</section>
See Also
--------
