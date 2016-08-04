This function parses a [JSON](/docs/JSON.md "wikilink") formatted string into variables. You can use [toJSON](/toJSON.md "wikilink") to encode variables into a JSON string that can be read by this function.

Syntax
------

``` lua
var fromJSON ( string json )
```

### Required Arguments

-   **json:** A JSON formatted string

### Returns

Returns variables read from the JSON string.

**Note:** Indices of a JSON object such as “1”: “cat” are being returned as [string](/docs/string.md "wikilink"), not as [integer](/int.md "wikilink").

Example
-------

This makes data equal: *{ \[“1”\] = “cat”, \[“2”\] = “mouse”, \[“3”\] = 5, \[“4”\] = null, \[“cat”\] = 5, \[“mouse”\] =1 }*

``` lua
local data = fromJSON ( '[ { "1": "cat", "2": "mouse", "3": 5, "4": null, "cat":5, "mouse":1 } ]' )
```

Example 2
---------

``` lua
local name, weapon, ammo = fromJSON("[\"Desert Eagle\", 24, 147]")
```

Requirements
------------

See Also
--------
