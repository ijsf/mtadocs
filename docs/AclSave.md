The ACL XML file is automatically saved whenever the ACL is modified, but the automatic save can be delayed by up to 10 seconds for performance reasons. Calling this function will force an immediate save.

Syntax
------

``` lua
bool aclSave ()
```

### Returns

Returns *true* if the ACL was successfully changed, *false* or *nil* if it could not be saved for some reason, ie. file in use.

Example
-------

This example saves the ACL when somebody types "/save-acl".

``` lua
function saveACL ( thePlayer, command ) -- Function header. Also where thePlayer is defined.
    local saved = aclSave() -- Save the ACL
        if ( saved ) then -- If it was successfully saved then...
            outputChatBox ( "ACL was successfully saved.", thePlayer, 255, 0, 0 ) -- Output it saved
        else -- If it wasn't saved for whatever reason then...
            outputChatBox ( "An unexpected error occured.", thePlayer, 255, 0, 0 ) -- Output it didn't save
        end
end
addCommandHandler ( "save-acl", saveACL ) -- Make it trigger for "/save-acl".
```

See Also
--------
