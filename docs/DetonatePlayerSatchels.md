This function detonates the thrown satchels of a player, as if they had fired the detonator. Please use [detonateSatchels](/detonateSatchels.md "wikilink") instead.

Syntax
------

``` lua
bool detonatePlayerSatchels( player thePlayer )         
```

### Required Arguments

-   **thePlayer:** the player that should have their thrown satchels detonated.

### Returns

Returns *true* if a valid player element was passed, false otherwise.

Example
-------

This example will allow players to detonate their thrown satchels via the command /detonate

``` lua
function cmdDetonateSatchels(plr)
    detonatePlayerSatchels(plr)
end
addCommandHandler("detonate", cmdDetonateSatchels)
```

Requirements
------------

See Also
--------
