This function returns the items selected in the specified [grid list](/docs/element/gui/gridlist.md "wikilink").

Syntax
------

``` lua
table guiGridListGetSelectedItems ( element gridList )
```

### Required Arguments

-   **gridList:** The [grid list](/docs/element/gui/gridlist.md "wikilink") which selected items you want to retrieve.

### Returns

Returns a table over the selected items in the [grid list](/docs/element/gui/gridlist.md "wikilink") in this format:

``` lua
table = {
    [1] = {
        ["column"], -- has the first selected item's column ID
        ["row"] -- has the first selected item's row ID
    },
    [2] = {
        ["column"],-- has the second selected item's column ID
        ["row"] -- has the second selected item's row ID
    },
    ...
}
```

if everything was successful or *false* if invalid arguments were passed.

Example
-------

``` lua
-- Todo...
```

See Also
--------

[Category:Needs Example](/docs/category:needs_example.md "wikilink")
