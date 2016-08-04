<pageclass class="client" subcaption="GUI Class method"></pageclass>

You can use this function to get theme by name.

Syntax
------

``` lua
dxTheme dxGetTheme ( themeName )
```

### Required Arguments

-   **themeName:** A name of the theme in **themes.xml**

### Returns

Returns a dxTheme if it is exists, false otherwise.

Example
-------

This example creates a window based on orange theme.

``` lua
local theme = dxGetTheme("Orange")
dxCreateWindow(....,theme)
```

See Also
--------

[Back to dxGUI page](/docs/dxGUI.md "wikilink")
