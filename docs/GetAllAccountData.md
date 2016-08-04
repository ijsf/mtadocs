This function returns a table containing all the user data for the [account](/account.md "wikilink") provided

Syntax
------

``` lua
table getAllAccountData ( account theAccount )
```

### Required Arguments

-   **theAccount:** The account you wish to retrieve all data from.

### Returns

A [table](/table.md "wikilink") containing all the user data. This table might be empty.

Example
-------

``` lua
function printAllData ( thePlayer )
    local playerAccount = getPlayerAccount( thePlayer ) -- get his account
    if ( playerAccount ) then -- if we got the account then
        local data = getAllAccountData( playerAccount ) -- get data
        count = 0
        for _ in pairs(data) do count = count + 1 end -- get the count
        outputChatBox ( "table holds " .. count .. " entries" ) -- output number of rows
        if ( data ) then
            for k,v in pairs ( data ) do
                outputChatBox(k..": "..v) -- print the key and value of each entry of data
            end
        end
    end
end
addCommandHandler( "getall", printAllData ) -- add a command handler for command 'getall'
```

Requirements
------------

See Also
--------
