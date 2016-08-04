This function changes the visible size of an object.

Syntax
------

``` lua
bool setObjectScale ( object theObject, float scale [, float scaleY, float scaleZ ] )
```

### Required Arguments

-   **theObject**: the [object](/object.md "wikilink") you wish to change the scale of.
-   **scale**: a float containing the new scale. 1.0 is the standard scale, with 0.5 being half the size and 2.0 being twice the size. If the scaleY is set, this will be scaleX.

### Optional Arguments

-   **scaleY**: a float containing the new scale on the Y axis
-   **scaleZ**: a float containing the new scale on the Z axis

### Returns

-   *true* if the scale was set properly.
-   *false* otherwise.

Example
-------

This example creates an antenna, and changes the size of it.

<section name="Client" class="client" show="true">
``` lua
-- get the position of the player
local x, y, z = getElementPosition(getLocalPlayer())
-- create the object
antenna = createObject (1595, x + 2, y, z )
if ( antenna ) then -- if it was created
    -- set the scale to half the normal scale
    setObjectScale ( antenna, 0.5)
    -- remove the collision
        setElementCollisionsEnabled (antenna, false)
end
```

</section>
See Also
--------
