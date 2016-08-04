<pageclass class="client" subcaption="GUI Class method"></pageclass>

You can use this function to get dxElement size.

Syntax
------

``` lua
float w, float h  dxGetSize (element dxElement, [bool relative = false])
```

### Required Arguments

-   **dxElement:** A dxGUI element.

### Optional Arguments

-   **relative:** This is whether sizes and positioning are relative. If this is *true*, script give relative w,h.

### Returns

-   **w**: An element width
-   **h**: An element height

Example
-------

This example gets window relative size.

``` lua

local w,h = dxGetSize(dxWindow,true)
outputChatBox(w.." "..h)
```

See Also
--------

[Back to dxGUI page](/docs/dxGUI.md "wikilink")
