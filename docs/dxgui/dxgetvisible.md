<pageclass class="client" subcaption="GUI Class method"></pageclass>

You can use this function to get dxElement visiblity.

Syntax
------

``` lua
dxElement  dxGetVisible (element dxElement)
```

### Required Arguments

-   **dxElement:** A dxGUI element.

### Returns

-   **visiblity**: dxGUI visiblity

Example
-------

This example gets window visiblity.

``` lua

local visiblity = dxGetVisible(dxWindow)
outputChatBox( tostring(visiblity) )
```

See Also
--------

[Back to dxGUI page](/docs/dxgui.md "wikilink")
