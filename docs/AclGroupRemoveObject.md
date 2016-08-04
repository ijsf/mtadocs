This function removes the given object (string) from the given ACL group. The object can be a resource or a player. See [aclGroupAddObject](/docs/aclGroupAddObject.md "wikilink") for more details.

Syntax
------

``` lua
bool aclGroupRemoveObject ( aclgroup theGroup, string theObjectString )
```

### Required Arguments

-   **theGroup:** The ACL group to remove the object string from
-   **theObjectString:** The object to remove from the ACL group

### Returns

Returns *true* if the object existed in the ACL and could be remoevd, *false* if it could not be removed for some reason, ie. it did not exist in the given ACL group.

Example
-------

This example does...

``` lua
function deladm (playerSource, commandName, accountName)
    if accountName then --Make the script able to detect if a user is given.
        aclGroupRemoveObject (aclGetGroup("Admin"), "user."..accountName) --Removing the admin.
        outputChatBox ("ACL: Account '"..accountName.."' succesfully removed as admin.", playerSource) -- Giving you a messsage.
        outputChatBox ("ACL: Someone have removed you as admin.", accountName) -- giving the poor removed guy a message.
    else --Make the Syntax display.
        outputChatBox ("ACL: No account name specified.", playerSource)
        outputChatBox ("ACL: Syntax: /deladmin [accountName]", playerSource)
    end
end
addCommandHandler ("deladmin", deladm)
```

See Also
--------
