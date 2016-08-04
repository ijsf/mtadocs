<lowercasetitle></lowercasetitle>

This function removes a specified value from a table.

Syntax
------

``` lua
bool table.removeValue( table theTable, string value )
```

### Required Arguments

-   **theTable**: The table you want to remove the specified value from.
-   **value**: The specified value you wish to remove.

### Returns

Returns the modified index the operation was successful, false if the specified value does not exist.

<section name="Code" class="both" show="true">
``` lua
function table.removeValue(table, val)
    for index, value in ipairs(table) do
        if value == val then
            table.remove(table, index)
            return index
        end
    end
    return false
end
```

</section>
Example
-------

<section name="Client Side" class="client" show="true">
``` lua
addEventHandler("onClientResourceStart",resourceRoot,
function()
    triggerServerEvent( "clientReady", resourceRoot )
end
)
```

</section>
<section name="Server Side" class="server" show="true">
``` lua
local readyPlayerList = {} -- Table

-- Add client to readyPlayerList table.
addEvent("clientReady", true )
addEventHandler("clientReady",resourceRoot,
function()
    table.insert( readyPlayerList, client )
end
)

-- Remove the quitting client's from the table.
function removePlayerFromTable ()
   table.removeValue( readyPlayerList, source )
end
addEventHandler("onPlayerQuit",root, removePlayerFromTable)
```

</section>
Author: Walid

See Also
--------
