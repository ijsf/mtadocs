This function returns the value of the specified statistic of a specific [ped](/docs/ped.md "wikilink").

Syntax
------

``` lua
float getPedStat ( ped thePed, int stat )
```

### Required Arguments

-   **thePed**: The [ped](/docs/ped.md "wikilink") whose stat you want to retrieve.
-   **stat**: A whole number determining the stat ID.

### Returns

Returns the value of the requested statistic.

Example
-------

<section name="Server" class="server" show="true">
This example announces whether a player is fat upon spawn

``` lua
function checkWeightOnSpawn ( )
    local stat = getPedStat ( source, 21 )
    -- Check that getPedStat returned a value
    if ( stat > 500 ) then
        -- Output the stat in the chat box
        outputChatBox ( getPlayerName ( source ) .. " needs to lose a bit of weight!" )
    end
end
addEventHandler ( "onPlayerSpawn", getRootElement(), checkWeightOnSpawn )
```

</section>
See Also
--------
