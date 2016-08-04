This function returns a table over all the objects that exist in a given ACL group. These are objects like players and resources.

Syntax
------

``` lua
table aclGroupListObjects ( aclgroup theGroup )
```

### Required Arguments

-   **theGroup:** The ACL group to get the objects from

### Returns

Returns a table of strings in the given ACL group. This table might be empty. Returns *false* or *nil* if theGroup is invalid or it fails for some other reason.

Example
-------

This example outputs a list of Objects if the ACL Group is given. (TESTED!)

``` lua
addCommandHandler("aclObjectList",function(player,command,aclGroup)
    if(aclGroup~="")then
        table = aclGroupListObjects(aclGetGroup(aclGroup))
        count = 0
        for objects,name in pairs(table)do
            outputChatBox("ACL LIST: "..aclGroup.." #"..tostring(count).." Object: "..name..".",player)
            count = count + 1
        end
    else
        outputChatBox("Please add the aclGroup you want the list of.",player)
        outputChatBox("Syntax: /aclObjectList aclGroup",player)
    end
end)
```

See Also
--------
