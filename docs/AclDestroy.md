This function destroys the ACL passed. The destroyed ACL will no longer be valid.

Syntax
------

``` lua
bool aclDestroy ( acl theACL )
```

### Required Arguments

-   **theACL:** The ACL to destroy

### Returns

Returns *true* if successfully destroyed and *false* if it could not be deleted (ie. it's not valid).

Example
-------

This example shows you a command to delete an ACL:

``` lua
function deleteSomeACL ( thePlayer, cmdname, theACL )
    if aclGet ( theACL ) then --Check if the specified ACL exists
        --If it does
        local deleted = aclDestroy ( theACL ) --Try to delete the ACL
        if deleted then --If the ACL has been deleted
            --We will give the player a succes-message
            outputChatBox ( "ACL " ..theACL.. " Succesfully removed!", thePlayer )
        else --If there was something wrong while deleting
            --We send the player an error message
            outputChatBox ( "Error while removing ACL " ..theACL.. "!", thePlayer )
        end
    else --If the ACL doesn't exists
        outputChatBox ( "Error: Invalid ACL Name specified, or the ACL doesn't exist.", thePlayer )
    end
end
addCommandHandler ( "deleteACL", deleteSomeACL ) --Add the commandhandler
```

See Also
--------
