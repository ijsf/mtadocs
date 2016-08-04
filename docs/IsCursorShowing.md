This function is used to determine whether or not a player's cursor is showing.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool isCursorShowing ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") you want to get cursor state of.

### Returns

Returns *true* if the player's cursor is showing, *false* if it isn't or if invalid parameters were passed.

</section>
<section name="Client" class="client" show="true">
``` lua
bool isCursorShowing ( )
```

### Returns

Returns *true* if the player's cursor is showing, *false* if it isn't.

</section>
Example
-------

<section name="Example" class="server" show="true">
This serverside function toggles a player's cursor state.

``` lua
function toggleCursor ( thePlayer )
    local currentState = isCursorShowing ( thePlayer )  -- get the current cursor state as a boolean
    local oppositeState = not currentState              -- get the new state as its logical opposite
    showCursor ( thePlayer, oppositeState )             -- set it as the new cursor state
end
```

</section>
<section name="Clientside Example" class="client" show="true">
With little of tweaking this can also be used clientside

``` lua
function toggleCursor ()
        local currentState = isCursorShowing ()  -- get the current cursor state as a boolean
        local oppositeState = not currentState              -- get the new state as its logical opposite
        showCursor ( oppositeState )             -- set it as the new cursor state
end
```

And a more compact version

    [lua]
    bindKey ("b", "down",                            -- binds B key to toggle cursor state
            function()
                    showCursor( not isCursorShowing() )
            end)

</section>
See Also
--------
