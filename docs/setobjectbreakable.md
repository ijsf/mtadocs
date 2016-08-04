This function sets an object to be breakable/unbreakable.

Syntax
------

``` lua
bool setObjectBreakable ( object theObject, bool breakable )
```

### Required Arguments

-   **object** the [object](/docs/object.md "wikilink") that's being set.
-   **breakable** a boolean whether the object is breakable(true) or unbreakable (false).

### Returns

-   *true* if the object is now breakable.
-   *false* if it can't or if invalid arguments are passed.

Example
-------

This example creates an object when the resource starts and sets it to be breakable.

``` lua
function toggleObjectVulnerability()
    local object = createObject(1337, 5540.6654, 1020.55122, 1240.545)
    if isObjectBreakable(object) then
        setObjectBreakable(object, false)
        outputChatBox("The object is now not breakable.")
    else
        setObjectBreakable(object, true)
        outputChatBox("The object is now breakable.")
    end
end
addEventHandler("onClientResourceStart", resourceRoot, toggleObjectVulnerability)
```

Requirements
------------

See Also
--------
