This function sets the vertical alignment of a text label.

Syntax
------

``` lua
bool guiLabelSetVerticalAlign ( element theLabel, string align )
```

### Required Arguments

-   **theLabel:** The text label to set the vertical alignment on.
-   **align:** The alignment type. Valid type strings are:
    -   “top”
    -   “center”
    -   “bottom”

### Returns

Returns *true* on success, *false* otherwise.

Example
-------

<section name="Example 1" class="client" show="true">
``` lua
local label = guiCreateLabel(300,200,100,500,"Text",false)
guiLabelSetVerticalAlign(label,"bottom")
```

</section>
See Also
--------
