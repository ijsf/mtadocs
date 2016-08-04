<pageclass class="#AA7592" subcaption="Texturizer Module"></pageclass>

Gets a table of the info about the GD libary which the module is compiled against.

Syntax
------

``` lua
table gd_info ( )
```

### Required arguments

### Returns

The following table of gd info:

` string `**`GD` `Version`**`: The version string of the GD libary the module is compiled against.`

Example
-------

**Example 1:** This example displays the gd version to joining players

``` lua
gdInfo = gd_info();

function gdVersion ( )
   outputDebugString(gdInfo["GD Version"], source);
end

addEventHandler("onPlayerJoin", getRootElement(), gdVersion)
```

See also
--------
