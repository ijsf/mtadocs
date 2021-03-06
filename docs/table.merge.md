<lowercasetitle></lowercasetitle>

This function merges two or more tables in the first.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **table1**: The table for merge.
-   **table2**: The table to merge from.

### Optional Arguments

-   **...**: The tables to merge from.

### Returns

Returns the first table merged with all the other.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function table.merge(table1,...)
    for _,table2 in ipairs({...}) do
        for key,value in pairs(table2) do
            if (type(key) == "number") then
                table.insert(table1,value)
            else
                table1[key] = value
            end
        end
    end
    return table1
end
```

</section>
Author: Lex128

See Also
--------
