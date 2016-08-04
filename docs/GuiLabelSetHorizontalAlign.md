This function sets the horizontal alignment of a text label.

Syntax
------

``` lua
bool guiLabelSetHorizontalAlign ( element theLabel, string align, [ bool wordwrap = false ] )
```

### Required Arguments

-   **theLabel:** The text label to set the horizontal alignment on.
-   **align:** The alignment type. Valid type strings are:
    -   “left”
    -   “center”
    -   “right”
-   **wordwrap:** Whether or not to enable wordwrap for the gui-label.

### Returns

Returns *true* on success, *false* otherwise.

Example
-------

<section name="Example 1" class="client" show="true">
``` lua
local label = guiCreateLabel(300,200,500,50,"Text",false)
guiLabelSetHorizontalAlign(label,"center")
```

</section>
See Also
--------
