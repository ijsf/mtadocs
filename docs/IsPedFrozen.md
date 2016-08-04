This function retrieves whether the pedestrian is frozen or not.

Syntax
------

``` lua
bool isPedFrozen ( ped thePed )
```

### Required Arguments

-   **thePed:** The [ped](/ped.md "wikilink") whose frozen state will be obtained.

### Returns

Returns a bool indicating the pedestrians frozen state, or *false* if invalid arguments were passed.

Example
-------

This example adds a 'togglefreeze' console command that lets players alternate their frozen state.

``` lua
function toggleFreeze ( sourcePlayer )
    setPedFrozen ( sourcePlayer, not isPedFrozen ( sourcePlayer ) )
end
addCommandHandler ( "togglefreeze", toggleFreeze )
```

See Also
--------
