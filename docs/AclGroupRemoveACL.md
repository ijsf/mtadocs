This function removes the given ACL from the given ACL group. (**Please NOTE:** The resource that's using this function needs the right to remove an acl.)

Syntax
------

``` lua
bool aclGroupRemoveACL ( aclgroup theGroup, acl theACL )
```

### Required Arguments

-   **theGroup:** The group to remove the given ACL from
-   **theACL:** The ACL to remove from the given group

### Returns

Returns *true* if the ACL was successfully removed from the ACL group, *false*/*nil* if it could not be removed for some reason, ie. either of the elements were invalid.

Example
-------

This example outputs to the console if the Admin acl was removed from the Moderator ACL Group. (TESTED!)

``` lua
addEventHandler("onResourceStart",resourceRoot,function()
    if(aclGroupRemoveACL(aclGetGroup("Moderator"),aclGet("Admin")))then
        aclSave()
        outputConsole("The Admin acl was removed from the Moderator group.")-- If it was successfully removed
    else
        outputConsole("Unsuccessful... Admin might have been removed from the Moderator group before.")-- if it was removed before or didn't existed
    end
end)    
```

See Also
--------
