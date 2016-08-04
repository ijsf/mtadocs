This function drops a table in the registry. This function doesn't do anything when the table doesn't exist.

The executed SQL query is the following:

``` sql
DROP TABLE <table>
```

Syntax
------

``` lua
bool executeSQLDropTable ( string tableName )
```

### Required Arguments

-   **tableName:** The name of the table you want to drop.

### Returns

The function returns *true* on success, and *false* on failure.

### Example

This example lets you drop an SQL table with the command: dropsqltable. Note: This command should be restricted to admins if you use it.

``` lua
function removeSQLTable(thePlayer, command, SQLtable)
    if (SQLtable) then -- Make sure the player entered an argument.
        success = executeSQLDropTable(SQLtable) -- Drop the table
        if (success) then -- If executeSQLDropTable returns true, it passes this if check to display a confirmation message
            outputChatBox("SQL Table "..SQLtable.." successfully dropped.", thePlayer, 0, 255, 0)
        else
            outputChatBox("SQL Table "..SQLtable.." was not successfully dropped.", thePlayer, 255, 0, 0)
        end
    end
end
addCommandHandler("dropsqltable", removeSQLTable)
```

See Also
--------
