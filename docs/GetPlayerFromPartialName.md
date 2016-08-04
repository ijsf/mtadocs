This function allows you to get player from their partial name.

Syntax
------

``` lua
player getPlayerFromPartialName ( string Name )
```

### Required Arguments

-   **Name**: A string containing the partial name of a player you want to reference.

### Returns

Returns a [player](/docs/player.md "wikilink") if the partial name exists, *nil* otherwise.

Code
----

    function getPlayerFromPartialName(name)
        local name = name and name:gsub("#%x%x%x%x%x%x", ""):lower() or nil
        if name then
            for _, player in ipairs(getElementsByType("player")) do
                local name_ = getPlayerName(player):gsub("#%x%x%x%x%x%x", ""):lower()
                if name_:find(name, 1, true) then
                    return player
                end
            end
        end
    end

**Author: TAPL**

See Also
--------
