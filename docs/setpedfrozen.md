Please use [setElementFrozen](/docs/setelementfrozen.md "wikilink")

This function freezes (or un-freezes) a pedestrian, meaning they cannot move, jump, aim, shoot, etcetera.

Syntax
------

<code lang="lua">\[lua,N\] bool setPedFrozen ( ped thePed, bool frozen )

</syntaxhighlight>
### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") whose frozen state will be changed.
-   **frozen:** A [bool](/docs/bool.md "wikilink") value as to whether the ped is frozen or not.

### Returns

Returns *true* if the frozen state was set successfully, or *false* if invalid arguments were passed.

Example
-------

This example adds a 'togglefreeze' console command that lets players alternate their frozen state.

``` lua
function toggleFreeze ( sourcePlayer )
    local frozen = getPedFrozen ( sourcePlayer )
    setPedFrozen ( sourcePlayer, not frozen )
end
addCommandHandler ( "togglefreeze", toggleFreeze )
```

See Also
--------

[ru:setPedFrozen](/docs/ru:setpedfrozen.md "wikilink")
