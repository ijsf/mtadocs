<pageclass class="client" subcaption="GUI Class method"></pageclass>

You can use this function to get default theme.

Syntax
------

``` lua
dxTheme dxGetDefaultTheme ( )
```

### Returns

Returns a dxTheme if it was successfully got which then can use other methods, false otherwise.

Example
-------

This example create a window based on an orange theme.And create a button based on default theme.

``` lua
local orange = dxGetTheme("Orange")
dxCreateWindow(....,orange)
local default = dxGetDefaultTheme()
dxCreateButton(....,default)
```

See Also
--------

[Back to dxGUI page](/docs/dxgui.md "wikilink")
