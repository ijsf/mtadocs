This function returns an [element](/element.md "wikilink") that corresponds to the current target of the specified player's camera (i.e. what it is following).

Syntax
------

<section class="server" name="Server" show="true">
``` lua
element getCameraTarget ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The player whose camera you wish to receive the target of.

</section>
<section class="client" name="Client" show="true">
``` lua
element getCameraTarget ()
```

</section>
### Returns

-   Returns an [element](/element.md "wikilink") of the target if the function was successful, or *false* if bad arguments were specified

Example
-------

This example checks whether a player's camera's target is another player, and returns true or false accordingly.

<section class="server" name="Server script" show="true">
``` lua
function isTargetPlayer( thePlayer )
    local target = getCameraTarget ( thePlayer )
    if ( getElementType ( target ) == "player" ) then   -- If target is a player
        return true                                     -- Return true
    else
        return false                                    -- Otherwise, return false.
    end
end
```

</section>
See Also
--------
