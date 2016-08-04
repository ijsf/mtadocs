This function brings a GUI element on top of others.

Syntax
------

``` lua
bool guiBringToFront ( element guiElement )
```

### Required Arguments

-   **guiElement:** the GUI element that you want to move to the front.

### Returns

Returns *true* if the function was successful, *false* otherwise.

Example
-------

This example creates a gui window and brings it on top.

``` lua
local window = guiCreateWindow ( 0.4, 0.4, 0.3, 0.3, "My dummy window", true )
guiBringToFront ( window )
```

See Also
--------
