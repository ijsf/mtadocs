Syntax
------

``` lua
string getUserdataType ( userdata value )
```

### Required Arguments

-   **value**: A userdata value to get the type of. Userdata types can be:
    -   **SHARED**
        -   *resource-data*: a [resource pointer](/docs/Resource.md "wikilink").
        -   *xml-node*: a [XML node](/docs/Xmlnode.md "wikilink").
        -   *lua-timer*: a [timer](/docs/timer.md "wikilink").
        -   *vector2*: a 2D vector, used in the [Vector2](/docs/Vector/Vector2.md "wikilink") class.
        -   *vector3*: a 3D vector, used in the [Vector3](/docs/Vector/Vector3.md "wikilink") class.
        -   *vector4*: a 4D vector, used in the [Vector4](/docs/Vector/Vector4.md "wikilink") class.
        -   *matrix*: a matrix, used in the [Matrix](/docs/Matrix.md "wikilink") class.
        -   *userdata*: a fallback userdata type return value, when no other type could be found for the object.
    -   **SERVER ONLY**
        -   *account*: a [player account](/docs/Account.md "wikilink").
        -   *db-query*: a [database query handle](/docs/dbQuery.md "wikilink").
        -   *acl*: an [ACL entry](/docs/ACL.md "wikilink").
        -   *acl-group*: an [ACL group](/docs/Aclgroup.md "wikilink").
        -   *ban*: a [player ban](/docs/Ban.md "wikilink").
        -   *text-item*: a [text display item](/docs/Textitem.md "wikilink").
        -   *text-display*: a [text display item](/docs/Textdisplay.md "wikilink").

### Returns

Returns a [string](/docs/string.md "wikilink") containing the specified userdata's type, or *false* plus an error message if the given value is not userdata.

Example
-------

This example shows a function that can be used to work around the impossibility to transfer vectors as arguments when using [triggerClientEvent](/docs/triggerClientEvent.md "wikilink") and [triggerServerEvent](/triggerServerEvent.md "wikilink"), by converting them into a table which can be used safely.

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
