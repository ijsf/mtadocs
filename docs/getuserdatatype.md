Syntax
------

``` lua
string getUserdataType ( userdata value )
```

### Required Arguments

-   **value**: A userdata value to get the type of. Userdata types can be:
    -   **SHARED**
        -   *resource-data*: a [resource pointer](/docs/resource.md "wikilink").
        -   *xml-node*: a [XML node](/docs/xmlnode.md "wikilink").
        -   *lua-timer*: a [timer](/docs/timer.md "wikilink").
        -   *vector2*: a 2D vector, used in the [Vector2](/docs/vector/vector2.md "wikilink") class.
        -   *vector3*: a 3D vector, used in the [Vector3](/docs/vector/vector3.md "wikilink") class.
        -   *vector4*: a 4D vector, used in the [Vector4](/docs/vector/vector4.md "wikilink") class.
        -   *matrix*: a matrix, used in the [Matrix](/docs/matrix.md "wikilink") class.
        -   *userdata*: a fallback userdata type return value, when no other type could be found for the object.
    -   **SERVER ONLY**
        -   *account*: a [player account](/docs/account.md "wikilink").
        -   *db-query*: a [database query handle](/docs/dbquery.md "wikilink").
        -   *acl*: an [ACL entry](/docs/acl.md "wikilink").
        -   *acl-group*: an [ACL group](/docs/aclgroup.md "wikilink").
        -   *ban*: a [player ban](/docs/ban.md "wikilink").
        -   *text-item*: a [text display item](/docs/textitem.md "wikilink").
        -   *text-display*: a [text display item](/docs/textdisplay.md "wikilink").

### Returns

Returns a [string](/docs/string.md "wikilink") containing the specified userdata's type, or *false* plus an error message if the given value is not userdata.

Example
-------

This example shows a function that can be used to work around the impossibility to transfer vectors as arguments when using [triggerClientEvent](/docs/triggerclientevent.md "wikilink") and [triggerServerEvent](/triggerServerEvent.md "wikilink"), by converting them into a table which can be used safely.

``` lua
function safeArgsForTransfer(...)
    local args = { ... }
    for index, arg in ipairs(args) do
        if type(arg) == "userdata" and getUserdataType(arg):match("vector") then
            -- Transform every kind of vector userdata to a table which can be transfered safely
            args[index] =
            {
                arg:getX(),
                arg:getY(),
                arg.getZ and arg:getZ() or nil,
                arg.getW and arg:getW() or nil,
                -- Extra field to distinguish from normal tables
                ["isVectorWorkaround"] = true
            }
        end
    end
    return unpack(args)
end
```

See Also
--------
