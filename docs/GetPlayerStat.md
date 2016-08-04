Description
-----------

This function returns a float that contains the value of the specified statistic, for a specific [player](/player.md "wikilink").

Syntax
------

``` lua
float getPlayerStat ( player thePlayer, int stat )
```

### Required Arguments

-   **thePlayer**: The [player](/player.md "wikilink") whose stat you want to retrieve.
-   **stat**: A whole number determining the stat ID.

### Returns

Returns a [float](/float.md "wikilink") indicating the statistic value.

Example
-------

<section name="Server" class="server" show="true">
This example announces whether a player is fat upon spawn

``` lua
function checkWeightOnSpawn ( spawnedPlayer )
    local stat = getPlayerStat ( spawnedPlayer, 21 )
    -- Check that getPlayerStat returned a value
    if ( stat > 500 ) then
        -- Output the stat in the chat box
        outputChatBox ( getClientName ( spawnedPlayer ) .. " needs to lose a bit of weight!" )
    end
end
addEventHandler ( "onPlayerSpawn", getRootElement(), checkWeightOnSpawn )
```

</section>
See Also
--------
