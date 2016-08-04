This function gets a [client](/docs/client.md "wikilink")'s name (a client can either be a [player](/player.md "wikilink") or an admin).

Syntax
------

``` lua
string getClientName ( client theClient )
```

### Required Arguments

-   **theClient:** the [client](/docs/client.md "wikilink") element (player or admin) you want to get the name of.

### Returns

Returns a *string* containing the requested client's name, or *false* if the client passed to the function is invalid.

Example
-------

This example adds a tag before a player's nick.

``` lua
function tagPlayer( thePlayer, tag )
    --we check thePlayer is a player, otherwise this function could be used with admins
    if getElementType(thePlayer) == "player" then
        --we store the player's current name,
        local oldName = getClientName( thePlayer )
        --append the tag passed to this function before it,
        local taggedName = tag .. oldName
        --then set it as his new name
        setClientName( thePlayer, taggedName )
    end
end
```

See Also
--------
