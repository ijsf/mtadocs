Get the name of given ACL.

Syntax
------

``` lua
string aclGetName ( acl theAcl )
```

### Required Arguments

-   **theACL:** The ACL to get the name of

### Returns

Returns the name of the given ACL as a string if successful. Returns *false*/*nil* if unsuccessful, ie the ACL is invalid.

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
