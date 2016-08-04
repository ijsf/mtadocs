This function adds the given ACL to the given ACL group. This makes the resources and players in the given ACL group have access to what's specified in the given ACL. The rights for something in the different ACL's in a group are OR-ed together, which means if one ACL gives access to something, this ACL group will have access to that.

Syntax
------

``` lua
bool aclGroupAddACL ( aclgroup theGroup, acl theACL )
```

### Required Arguments

-   **theGroup:** The group to add the ACL to
-   **theACL:** The ACL to add to the group

### Returns

Returns *true* if the ACL could be successfully added to the ACL group, *false*/*nil* if either of the elements are invalid, the ACL is already in that group or if something else goes wrong.

Example
-------

This example adds a command *addAclGroup* with which you can easily add new access control lists to specified acl Groups.

``` lua
function addAclGroup ( thePlayer, commandName, aclName )
if(aclName) then
    acl = aclCreate ( aclName )
else
    acl = aclCreate("myName")
end
aclGroup = aclGetGroup("Admin")
aclGroupAddACL(aclGroup,acl) -- now all Admins have the rights of acl, too
aclSave () 
addCommandHandler ( "addAclGroup", addAclGroup)
```

See Also
--------
