This function is used to get the name of the given ACL group.

Syntax
------

``` lua
string aclGroupGetName ( aclgroup aclGroup )
```

### Required Arguments

-   **aclGroup:** The ACL group to get the name of

### Returns

Returns the name of the given ACL group as a string if successfull, *false*/*nil* if the aclGroup is invalid or it fails for some other reason.

Example
-------

This example outputs to the console that “Admin's are ready to watch”.

``` lua
addEventHandler("onResourceStart",resourceRoot,function()
    outputConsole(aclGroupGetName(aclGetGroup("Admin")).."'s are ready to watch :)",root)
end)
```

See Also
--------
