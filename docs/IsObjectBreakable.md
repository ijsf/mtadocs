This function checks if an object is breakable.

Syntax
------

``` lua
bool isObjectBreakable ( object theObject )
```

### Required Arguments

-   **object** the [object](/object.md "wikilink") that's being checked.

### Returns

-   *true* if the object is breakable.
-   *false* if the object is not breakable.

Example
-------

This example creates an object when the resource starts and checks if the object is breakable.

``` lua
addEventHandler("onClientResourceStart",resourceRoot,function()
    local object = createObject ( 1337, 5540.6654, 1020.55122, 1240.545 )
    if isObjectBreakable(object) then
        outputChatBox("Yes, the object is breakable.")
    else
        outputChatBox("No, the object is not breakable")
    end
end)
```

Requirements
------------

See Also
--------
