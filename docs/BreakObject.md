This function breaks a specific object. Note: Only breakable objects can be broken.

Syntax
------

``` lua
bool breakObject ( object theObject )
```

### Required Arguments

-   **theObject:** an [object](/object.md "wikilink") element

### Returns

-   *true* if the object was successfully broken.
-   *false* if the object is not breakable, or a wrong object was given.

Example
-------

This example checks if the object created is breakable and if it is then breaks it.

``` lua
addCommandHandler("createObj",
function(command, id)
    local x, y, z = getElementPosition(localPlayer)
    local object = createObject (id, x, y, z)
    if (id) then
        if isObjectBreakable(object) then
            breakObject(object)
        end
    end
end
)
```

See Also
--------
