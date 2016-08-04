This function returns a list of all the ACLs.

Syntax
------

``` lua
table aclList ()
```

### Returns

Returns a table of all the ACLs. This table can be empty if no ACLs exist. It can also return *false*/*nil* if it failed for some reason.

Example
-------

This example adds a command *listacls* which prints out a name list of all ACLs to the console.

``` lua
function printOutAllACLs ( thePlayer )
    -- get a table over all the ACLs
    local allACLs = aclList()
    -- if the table is empty (there are no ACLs)
    if #allACLs == 0 then
        -- print out a message to console and exit function
        return outputConsole ( "There are no ACLs!", thePlayer )
    else
        -- print out a list of the names
        outputConsole ( "List of all ACLs:", thePlayer )
        for key, singleACL in ipairs ( allACLs ) do
            local ACLName = aclGetName ( singleACL )
            outputConsole ( "- " .. tostring ( ACLName ), thePlayer )
        end
   end
end
addCommandHandler ( "listacls", printOutAllACLs )
```

See Also
--------
