<lowercasetitle></lowercasetitle>

This function copies a whole table and all the tables in that table instead of just linking to it.

Syntax
------

``` lua
table table.copy( table tab, bool recursive=false )
```

### Required Arguments

-   **tab**: The table to copy.
-   **recursive**: Whether sub-tables should be copied as well

### Returns

Returns a new table with the same content as tab has.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function table.copy(tab, recursive)
    local ret = {}
    for key, value in pairs(tab) do
        if (type(value) == "table") and recursive then ret[key] = table.copy(value)
        else ret[key] = value end
    end
    return ret
end
```

</section>
Author: NeonBlack

See Also
--------
