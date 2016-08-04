<lowercasetitle/>

This function is used to rename an [ACL group](/docs/aclgroup.md "wikilink").

Syntax
------

``` Lua
bool renameAclGroup ( string old, string new )
```

Required Arguments
------------------

-   **old:** name of the ACL group you want to change
-   **new:** the name we want the group to be changed to

### Returns

Returns *true* if the rename was successful, *false* otherwise.

Code
----

<section name="Server" class="server" show="true">
    function renameAclGroup( old, new )
        if ( type( old ) ~= "string" ) then
            outputDebugString( "Bad argument 1 @ renameAclGroup [ string expected, got " .. type( old ) .. " ] ", 2 )
            return false
        end
        
        if ( type( new ) ~= "string" ) then
            outputDebugString( "Bad argument 2 @ renameAclGroup [ string expected, got " .. type( new ) .. " ] ", 2 )
            return false
        end
        
        local oldACLGroup = aclGetGroup( old )
        
        if ( not oldACLGroup ) then
            outputDebugString( "Bad argument 1 @ renameAclGroup [ no acl group found with this name ] ", 2 )
            return false
        end
        
        if ( aclGetGroup( new ) ) then
            outputDebugString( "Bad argument 2 @ renameAclGroup [ there is already a group with this name ] ", 2 )
            return false
        end
        
        local oldACL = aclGroupListACL( oldACLGroup )
        local oldObjects = aclGroupListObjects( oldACLGroup )
        local newACLGroup = aclCreateGroup( new )
        
        for _,nameOfACL in pairs( oldACL ) do
            aclGroupAddACL( newACLGroup, nameOfACL )
        end
        
        for _,nameOfObject in pairs( oldObjects ) do
            aclGroupAddObject( newACLGroup, nameOfObject )
        end
        
        aclDestroyGroup( oldACLGroup )
        aclSave( )
        aclReload( )
        
        return true
    end

</section>
-   Original author: *Has\[S\]oN*
-   Skype: *hassan.saad2000*

Example
-------

This example changes a group named *Moderator* to *HassoN* when the script is loaded.

<section name="Server" class="server" show="true">
    addEventHandler( "onResourceStart", resourceRoot,
        function( )
            renameAclGroup( "Moderator", "HassoN" )
        end
    )

</section>
See also
--------
