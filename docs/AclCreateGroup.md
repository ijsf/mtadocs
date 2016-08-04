This function creates a group in the ACL. An ACL group can contain objects like players and resources. They specify who has access to the ACL's in this group.

Syntax
------

``` lua
aclgroup aclCreateGroup ( string groupName )
```

### Required Arguments

-   **groupName:** The name of the group to create

### Returns

Returns the pointer to the created aclgroup if successful. Returns false if failed.

Example
-------

This example adds a command *addobjecttogroup* with which you can easily add new objects to specified access control list groups.

``` lua
function addACLGroupObject ( thePlayer, commandName, groupName, objectName )
    local ourGroup = aclGetGroup ( groupName )
    -- if there is no previous group with this name, we need to create one
    if not ourGroup then
        ourGroup = aclCreateGroup ( groupName )
    end

    -- if object name wasn't given
    if not objectName then
        -- print out message to chatbox
        return outputChatBox ( "You need to specify the object!", thePlayer )
    end

    -- and finally let's add the object to it's group
    aclGroupAddObject ( ourGroup, objectName )
    -- don't forget to save the ACL after it has been modified
    aclSave ()
end
addCommandHandler ( "addobjecttogroup", addACLGroupObject )
```

See Also
--------
