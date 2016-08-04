This function is used to remove a ped's jetpack.

Syntax
------

``` lua
bool removePedJetPack ( ped thePed )
```

### Required Arguments

-   **thePed**: The [ped](/ped.md "wikilink") you want to remove the jetpack from.

### Returns

Returns *true* if the ped had a jetpack, *false* otherwise.

Example
-------

This example adds a “jetpack” command in console, which allows toggling of a jetpack.

``` lua
function jetPackCommand ( source, key )
    if ( doesPedHaveJetPack ( source ) ) then     -- if the player has a jetpack
        removePedJetPack ( source )               -- remove it
    else
        givePedJetPack ( source )                 -- otherwise give him one
    end
end
addCommandHandler ( "jetpack", jetPackCommand )
```

See Also
--------
