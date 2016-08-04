This function adds an object to the given ACL group. An object can be a player's account, specified as:

` `*`user.`<accountname>*

Or a resource, specified as:

` `*`resource.`<resourcename>*

Objects are specified as strings. The ACL groups work for the user accounts and the resources that are specified in them.

Syntax
------

``` lua
bool aclGroupAddObject ( aclgroup theGroup, string theObjectName )
```

### Required Arguments

-   **theGroup:** The group to add the object name string too.
-   **theObjectName:** The object string to add to the given ACL.

### Returns

Returns *true* if the object was successfully added to the ACL, *false* if it already existed in the list.

Example
-------

This example makes every player able to use a command named “giveAccountAdminRights” that will add a specific accountname as an ACL object to the “Admin” group.

``` lua
function giveAdminRights (playerSource, commandName, accountName) --add the function giveAdminRights and specify its arguments
    if accountName then --if there was an accountName entered then
        aclGroupAddObject (aclGetGroup("Admin"), "user."..accountName) --add an ACL object using the form "user.[accountName]" to the ACL group "Admin"
        outputChatBox ("Account '"..accountName.."' succesfully added to the admin group", playerSource) --output a notification to the player who entered the command that the acocunt was successfully added
    else --else output an error message and the correct syntax of the command to the player who entered it
        outputChatBox ("No account name specified.", playerSource)
        outputChatBox ("Correct syntax: /giveAccountAdminRights [accountName]", playerSource)
    end
end

addCommandHandler ("giveAccountAdminRights", giveAdminRights) --add a command "giveAccountAdminRights" and attch the function "giveAdminRights" to it 
```

See Also
--------
