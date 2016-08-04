Makes an object static or non-static. Static objects are rock solid in one place, unaffected by gravity and pushing. Nonstatic objects can fall, be pushed around etc.

**Note1:** Not all objects that are static by default can be made nonstatic.<br\> **Note2:** Dynamic objects with a “destroyed” state are still destroyable. Use [isElementOnScreen](/isElementOnScreen.md "wikilink") to detect, destroy, and recreate these objects.

Syntax
------

``` lua
bool setObjectStatic ( object theObject, bool toggle )
```

### Required Arguments

-   **theObject:** the object whose behaviour you want to change.
-   **toggle:** *true* makes the object static, *false* makes it nonstatic.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

See Also
--------
