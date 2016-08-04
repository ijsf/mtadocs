<lowercasetitle></lowercasetitle>

This function get all groups from player.

Syntax
------

``` lua
Groups getPlayerAllGroups ( element Player)
```

### Return

Returns a [Groups](/docs/Groups.md "wikilink") else false.

Code
----

``` lua

function getPlayerAllGroups(player)
    local account = getPlayerAccount ( player)
    if ( isGuestAccount ( account ) ) then
        return false
    end
                  local  AclList = {}
                                  AclList["Groups"] = {}
                  AclList["getGroups"] = {}
        for _, group in ipairs ( aclGroupList() ) do
                table.insert ( AclList["Groups"],aclGroupGetName ( group ) )
        end
        for k ,v in pairs(AclList.Groups) do
            if isObjectInACLGroup ( "user."..getAccountName ( account ), aclGetGroup (v) ) then
                table.insert ( AclList["getGroups"],v)
            end
        end
        return table.concat(AclList.getGroups, ",")
end
```

Example
-------

<section name="Example" class="both" show="true">
``` lua
-- A simple example:
```

</section>
Author: Booo
