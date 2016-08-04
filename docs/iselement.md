This function checks if a value is an [element](/docs/element.md "wikilink") or not.

Syntax
------

``` lua
bool isElement ( var theValue )
```

### Required Arguments

-   **theValue**: The value that we want to check.

### Returns

Returns *true* if the passed value is an element, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This serverside function kills a player when it's passed his name or his element.

``` lua
function killPlayer2 ( argument )
    -- if the argument is an element, and also a player,
    if isElement( argument ) and getElementType( argument ) == "player" then
        -- kill him
        killPed ( argument )

    -- if it isn't an element, but a string, it could be a name
    elseif type ( argument ) == "string" then
        -- retrieve the player with that name
        local playerElement = getPlayerFromName( argument )
        -- if a player with such a name exists,
        if playerElement then
            -- kill him
            killPed ( playerElement )
        end
    end
end
```

</section>
See Also
--------
