This function checks the progress of a database query.

Syntax
------

``` lua
table dbPoll ( handle queryHandle, int timeout[, bool multipleResults = false ] )
```

### Required Arguments

-   **queryHandle:** A query handle previously returned from [dbQuery](/docs/dbquery.md "wikilink")
-   **timeout:** How many milliseconds to wait for a result. Use 0 for an instant response (which may return nil). Use -1 to wait until a result is ready. Note: A wait here will freeze the entire server just like the executeSQL\* functions

### Optional Arguments

### Returns

-   *nil:* Returns nil if the query results are not yet ready. You should try again in a little while. (If you give up waiting for a result, be sure to call [dbFree](/docs/dbfree.md "wikilink"))
-   *false:* Returns false if the query string contained an error, the connection has been lost or the query handle is incorrect. This automatically frees the query handle, so you do not have to call [dbFree](/docs/dbfree.md "wikilink").
    -   This also returns two extra values: (See the example on how the retrieve them)
        -   *int:* error code
        -   *string* error message
-   *table:* Returns a table when the query has successfully completed. This automatically frees the query handle, so you do not have to call [dbFree](/docs/dbfree.md "wikilink").
    -   This also returns extra values:
        -   *int:* number of affected rows (Only if multipleResults is false)
        -   *int:* last insert id (Only if multipleResults is false)

Example
-------

This example waits until a result is ready:

``` lua
local result = dbPoll ( qh, -1 )
```

This example shows the possible return values:

``` lua
local result, num_affected_rows, last_insert_id = dbPoll ( qh, -1 )

if result == nil then
    outputConsole( "dbPoll result not ready yet" )
elseif result == false then
    local error_code,error_msg = num_affected_rows,last_insert_id
    outputConsole( "dbPoll failed. Error code: " .. tostring(error_code) .. "  Error message: " .. tostring(error_msg) )
else
    outputConsole( "dbPoll succeeded. Number of affected rows: " .. tostring(num_affected_rows) .. "  Last insert id: " .. tostring(last_insert_id) )
end
```

This example shows how to handle the result if the query selected data:

``` lua
local result = dbPoll ( qh, -1 )

if result then
    for _, row in ipairs ( result ) do

        -- by using a second loop (use it if you want to get the values of all columns the query selected):
        for column, value in pairs ( row ) do
            -- column = the mysql column of the table in the query
            -- value = the value of that column in this certain row
        end
        
        -- or without a second loop (use it if you want to handle every value in a special way):
        outputChatBox ( row["column"] ) -- it will output the value of the column "column" in this certain row
    end
end
```

Requirements
------------

Changelog
---------

See Also
--------
