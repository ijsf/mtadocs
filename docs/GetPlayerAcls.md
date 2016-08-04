<lowercasetitle></lowercasetitle>

This function returns a table over all the ACL's Player.

Syntax
------

``` lua
table getPlayerAcls ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The Player to get the ACL's elements from

### Returns

Returns a *table* over the *string*. This table might be empty if player invalid or player account is guest.

Code
----

``` lua
function getPlayerAcls(thePlayer)
    local acls = {}
    local account = getPlayerAccount(thePlayer)
    if (account) and not (isGuestAccount(account)) then
        local accountName = getAccountName(account)
        for i,group in ipairs(aclGroupList()) do
            if (isObjectInACLGroup( "user." ..accountName, group)) then
                local groupName = aclGroupGetName(group)
                table.insert(acls, groupName)
            end
        end
    end
    return acls
end
```

Example
-------

<section name="Serverside script" class="server" show="true">
This example outputs the list of ACL's player

``` lua
addCommandHandler("getacls",
function (thePlayer)
    local acl = getPlayerAcls(thePlayer)
    outputChatBox("You're in the following ACL groups: ".. tostring( table.concat(acl, ", ") ), thePlayer, 255, 0, 0)
end)
```

</section>
Credits
-------

-   **Author:**: WASSIm.

See Also
--------
