Use this to define whether the player's name tag is visible or invisible.

Syntax
------

``` lua
bool setPlayerNametagShowing ( player thePlayer, bool showing )
```

### Required Arguments

-   **thePlayer:** Define the player whos tag visiblity status you want to change
-   **showing:** Use true or false to show/hide the tag

### Returns

Returns *true* if successful, *false* otherwise

Example
-------

This script will turn off player tags for everyone

``` lua
function onResourceStart ( )
    local players = getElementsByType ( "player" ) -- Store all the players in the server into a table
    for key, player in ipairs ( players ) do       -- for all the players in the table
        setPlayerNametagShowing ( player, false )  -- turn off their nametag
    end
end
addEventHandler ( "onResourceStart", resourceRoot, onResourceStart )

function onPlayerJoin ( )
      -- Whoever joins the server should also have their nametags deactivated
    setPlayerNametagShowing ( source, false )
end
addEventHandler ( "onPlayerJoin", root, onPlayerJoin )
```

See Also
--------

[ar:setPlayerNametagShowing](/docs/ar:setPlayerNametagShowing.md "wikilink")
