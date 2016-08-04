<lowercasetitle></lowercasetitle>

This function splits a string at a given separator (pattern) and stores the pieces in a table. It's the complement of [table.concat](http://www.lua.org/manual/5.1/manual.html#pdf-table.concat).

There is already an MTA function called [split](/docs/split.md "wikilink") that splits a string at a given separator. But this function only supports single character separators and no regular expressions. For splitting at a single character you should prefer that function since it's probably faster than string.explode.

Syntax
------

``` lua
table string.explode( string ensemble, string separator )
```

### Required Arguments

-   **ensemble**: The string to split.
-   **separator**: The regular expression pattern, which the ensemble should be split at.

### Returns

Returns a table containing the pieces of the split ensemble.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function string.explode(self, separator)
    Check("string.explode", "string", self, "ensemble", "string", separator, "separator")

    if (#self == 0) then return {} end
    if (#separator == 0) then return { self } end

    return loadstring("return {\""..self:gsub(separator, "\",\"").."\"}")()
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example sends a welcome message to a player e.g. when joining a roleplay server.

``` lua
-- get the root element
local _root = getRootElement()
-- define the onPlayerJoin handler function
function OnPlayerJoin()
    -- get the player's name
    local playername = getPlayerNametagText(source)
    -- split the player's name to first and last name
    playername = playername:explode("%.") -- since . is a wildcard we have to escape it with a %
    -- send a welcome message
    outputChatBox("Welcome on our roleplay server, Mr./Mrs./Ms. "..playername[2]..".", source)
end
-- add the event handler
addEventHandler("onPlayerJoin", _root, OnPlayerJoin)
```

</section>
Author: NeonBlack

See Also
--------
