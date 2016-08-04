This function removes the given right (string) from the given ACL.

Syntax
------

``` lua
bool aclRemoveRight ( acl theAcl, string rightName ) 
```

### Required Arguments

-   **theAcl:** The ACL to remove the right from
-   **rightName:** The ACL name to remove from the right from

### Returns

Returns *true* if the given right was successfully removed from the given ACL, *false* or *nil* if it could not be removed for some reason, ie. it didn't exist in the ACL.

Example
-------

This example removes an acl right on resource start.

``` lua
addEventHandler("onResourceStart",resourceRoot,function()
   aclRemoveRight(aclGet("Admin"),"function.setServerPassword")
end)
```

See Also
--------
