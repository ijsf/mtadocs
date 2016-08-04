Get the ACL with the given name. If need to get most of the ACL's, you should consider using [aclList](/docs/aclList.md "wikilink") to get a table of them all.

Syntax
------

``` lua
acl aclGet ( string aclName )
```

### Required Arguments

-   **aclName:** The name to get the ACL belonging to

### Returns

Returns the ACL with that name if it could be retrieved, *false*/*nil* if the ACL does not exist or it fails for some other reason.

Example
-------

This example adds a command *setaclright* with which you can easily add new rights to specified access control lists.

``` lua
function setACLRight ( thePlayer, commandName, aclName, rightName, access )
    local ourACL = aclGet ( aclName )
    -- if there is no previous ACL with this name, we need to create one
    if not ourACL then
        ourACL = aclCreate ( aclName )
    end

    -- turn the boolean string to lower case
    access = string.lower ( access )
    -- access has to be either true or false (booleans)
    if not (access == "true" or access == "false") then
        -- print out error message to debug window
        return outputDebugString ( "Invalid access; true and false are only accepted", 1 )
    end

    -- change the access to boolean
    if access == "true" then
        access = true
    else 
        access = false
    end

    -- and finally let's set the right
    aclSetRight ( ourACL, rightName, access )
    -- don't forget to save the ACL after it has been modified
    aclSave ()
end
addCommandHandler ( "setaclright", setACLRight )
```

See Also
--------
