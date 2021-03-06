This function returns true if the player is in the ACL group, false if otherwise.

Syntax
------

``` lua
bool isPlayerInACL ( player thePlayer, string ACLGroup )
```

### Required Arguments

-   **thePlayer**: The player element that you want to check
-   **ACLGroup**: The name of the ACL group that you want to check

**Important Note**: This function will only work on the server-side.

### Returns

Returns true if the player's account is in the ACL, false if otherwise.

Code
----

``` lua
function isPlayerInACL ( player, acl )
    local account = getPlayerAccount ( player )
    if ( isGuestAccount ( account ) ) then
        return false
    end
        return isObjectInACLGroup ( "user."..getAccountName ( account ), aclGetGroup ( acl ) )
end
```

Example
-------

This is an example of the function.

``` lua
function checkAccess(thePlayer)
 if isPlayerInACL(thePlayer, "Console") then
  outputChatBox("Access Granted!")
   else
  outputChatBox("Access Denied!")
 end
end
addCommandHandler("myaccess", checkAccess)
```

xXMADEXx

See Also
--------
