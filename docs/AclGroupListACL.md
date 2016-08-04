This function returns a table over all the ACL's that exist in a given ACL group.

Syntax
------

``` lua
table aclGroupListACL ( aclgroup theGroup )
```

### Required Arguments

-   **theGroup:** The ACL group to get the ACL elements from

### Returns

Returns a table of the ACL elements in the given ACL group. This table might be empty. Returns *false* or *nil* if theGroup is invalid or it fails for some other reason.

Example
-------

This example outputs the list of ACL's if the aclGroup name is given. (TESTED!)

``` lua
addCommandHandler("aclList",function(player,command,aclGroup)
    if(aclGroup~="")then
        tables = aclGroupListACL(aclGetGroup(aclGroup))
        count = 0
        for list,nam in pairs(tables) do
            outputChatBox("ACL LIST: "..aclGroup.."Line: "..tostring(count).." ACL: "..aclGetName(nam)..".",player)
            count = count + 1
        end
    else
        outputChatBox("Please add the aclGroup you want the list of.",player)
        outputChatBox("Syntax: /aclList aclGroup",player)
    end
end)
```

See Also
--------
