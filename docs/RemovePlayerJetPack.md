This function is used to remove a player's jetpack.

Syntax
------

``` lua
bool removePlayerJetPack ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/docs/player.md "wikilink") you want to remove the jetpack from.

### Returns

Returns *true* if the player had a jetpack, *false* otherwise.

Example
-------

This example adds a “jetpack” command in console, which allows toggling of a jetpack.

``` lua
function jetPackCommand ( source, key )
    if ( doesPlayerHaveJetPack ( source ) ) then  -- if the player has a jetpack
        removePlayerJetPack ( source )            -- remove it
    else
        givePlayerJetPack ( source )              -- otherwise give him one
    end
end
addCommandHandler ( "jetpack", jetPackCommand )
```

See Also
--------
