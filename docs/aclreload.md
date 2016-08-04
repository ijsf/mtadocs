This function reloads the ACL's and the ACL groups from the ACL XML file. All ACL and ACL group elements are invalid after a call to this and should not be used anymore.

Syntax
------

``` lua
bool aclReload ()
```

### Returns

Returns *true* if the XML was successfully reloaded from the file, *false* or *nil* if the XML was invalid, didn't exist or could not be loaded for some other reason.

Example
-------

This example allows an admin to reload the ACL by typing "/reloadACL".

``` lua
function reloadACL ( source, command )
-- Check if they're an admin...
    if ( isObjectInACLGroup ( "user." .. getAccountName ( getPlayerAccount ( source )), aclGetGroup ( "Admin" ) ) ) then
        local reload = aclReload() -- Reload the ACL
            if ( reload ) then -- Check it was reloaded successfully
                outputChatBox ( "ACL was successfully reloaded.", source, 255, 0, 0 ) -- If so, output it
            else -- If not, output it (line below)
                outputChatBox ( "An unknown error occured. Please check the ACL file exists.", source, 255, 0, 0 )
            end
    else -- If they're not an admin, output it (below)
        outputChatBox ( "You must be an admin to use this command!", source, 255, 0, 0 )
    end
end
addCommandHandler ( "reloadACL", reloadACL )
```

See Also
--------
