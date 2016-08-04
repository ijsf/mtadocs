This function gets players who have data name you passed to it.

Syntax
------

``` lua
table getPlayersByData ( data name )
```

### Required Arguments

-   **data name**: A string determining the data you wish to get players from.

### Returns

Returns a table containing players who have the data name *false* if no player has this data name or the data name is invalid.

**Note:** Returns false if no player in the server has the data name.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getPlayersByData(dataName)
    if dataName and type(dataName) == "string" then
    local playersTable = {}
    for i,v in ipairs(getElementsByType("player")) do
        if getElementData(v, dataName) then
                table.insert(playersTable, v)
        end
    end
    if #playersTable == 0 then
        return false
    end
    return playersTable
    else
        return false
    end
end
```

</section>
Example
-------

<section name="Client" class="client" show="true">
This example outputs every player who have the certain data name.

``` lua
function gettingData(cmd, dataName)
    if not dataName then return outputChatBox("[Syntax] /getData [data name]", 255) end
    local players = getPlayersByData(dataName)
    if players then
        for i,v in ipairs(players) do
         outputChatBox(getPlayerName(v) .. " has '" .. dataName .. "' data.")
        end
    else
        outputChatBox("Invalid data name or no player has this data name!", 255, 0, 0)
    end
end
addCommandHandler("getData", gettingData)
```

</section>
Author: Tete

See Also
--------
