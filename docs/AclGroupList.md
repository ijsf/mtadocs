This function returns a table of all the ACL groups.

Syntax
------

``` lua
table aclGroupList ()
```

### Returns

Returns a table of all the ACL groups if successful, returns an empty table if no ACL groups exist. *false*/*nil* can be returned if this function fails for some other reason.

Example
-------

This example shows, how to output all ACL Group Names by *showAclGroups*

``` lua
function showGroups(player)
    local groups = {}
    groups = aclGroupList()
    for i,v in ipairs(groups) do
        local name = aclGroupGetName(v)
        outputChatBox(tostring(name),player)
    end
end
addCommandHandler("showAclGroups",showGroups)
```

See Also
--------
