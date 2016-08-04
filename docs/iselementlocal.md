This function checks whether a clientside [element](/docs/element.md "wikilink") is local to the client (doesn't exist in the server) or not.

Syntax
------

``` lua
bool isElementLocal ( element theElement )
```

### Required Arguments

-   **theElement**: The [element](/docs/element.md "wikilink") that we want to check.

### Returns

Returns *true* if the passed element is local, *false* if not or if invalid parameters are passed.

Example
-------

This clientside function destroys all local radar blips.

``` lua
function destroyAllLocalBlips ( )
    -- get a table containing all blips
    local allBlips = getElementsByType( "blip" )
    -- for each blip in this table,
    for index, theBlip in ipairs ( allBlips ) do
        -- check if it's a blip that only exists locally,
        if isElementLocal ( theBlip ) then
            -- and destroy it in that case
            destroyElement ( theBlip )
        end
    end
end
```

See Also
--------
