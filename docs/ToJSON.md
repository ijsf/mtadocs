This function converts a **single** value (preferably a Lua table) into a [JSON](/JSON.md "wikilink") encoded string. You can use this to store the data and then load it again using [fromJSON](/fromJSON.md "wikilink").

Syntax
------

``` lua
string toJSON ( var value, [ bool compact = false ][, string prettyType = "none" ] )
```

### Required Arguments

-   **var:** An argument of any type. Arguments that are elements will be stored as element IDs that are liable to change between sessions. As such, do not save elements across sessions as you will get unpredictable results.

### Optional Arguments

### Returns

Returns a JSON formatted string.

Example
-------

This example shows how you can encode an array. The string json should equal ''"\[ { “1”: “dogs”, “mouse”: “food”, “cat”: “hungry”, “birds”: 4 } \]" after executed.

``` lua
local json = toJSON ( { "dogs", cat = "hungry", mouse = "food", birds = 4 } )
```

Requirements
------------

See Also
--------
