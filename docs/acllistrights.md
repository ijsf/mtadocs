This function returns a table of all the rights that a given ACL has.

Syntax
------

``` lua
table aclListRights ( acl theACL, string allowedType )
```

### Required Arguments

-   **theACL:** The ACL to get the rights from
-   **allowedType:** The allowed right type. Possible values are *general*, *function*, *resource* and *command*

### Returns

Returns a table over the rights as strings in the given ACL. This table might be empty. Returns *false* or *nil* if theACL is invalid or it fails for some other reason.

Example
-------

This example outputs the rights of the given acl. (TESTED!)

``` lua
addCommandHandler("aclRights",function(player,command,theAcl)
    if(theAcl~="")then
        rights = aclListRights(aclGet(theAcl))
        count = 0
        for acl,list in pairs(rights)do
            outputChatBox("ACL List: "..theAcl.." #"..tostring(count).." Right: "..list..".",player)
            count = count + 1
        end
    else
        outputChatBox("Please type in a acl that you want to retrieve the rights from.",player)
        outputChatBox("Please use this Syntax: /aclRights theACL ",player)
    end
end)
```

See Also
--------
