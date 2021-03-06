<lowercasetitle></lowercasetitle>

This function goes through a table and replaces every field with the return of the passed function, where the field's value is passed as first argument and optionally more arguments. It's also possible to enable mapping of tables that are stored in the given table.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **tab**: The table to map.
-   **depth**: An integer specifying how deep the table should be mapped. If depth is for example 1 table.map will map the passed table and all tables that are in that given table but not those who are in a table that is in the passed table.
-   **func**: The function that should be called for every field of the table. This function should return something.

### Optional Arguments

-   **argument1, ...**: All arguments that should be passed to func everytime it's called.

### Returns

Returns a table with the values returned by func for every field.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function table.map(tab, depth, func, ...)
    for key, value in pairs(tab) do
        if (type(value) == "table" and depth ~= 0) then tab[key] = table.map(value, depth - 1, func, ...)
        else tab[key] = func(value, ...) end
    end
    return tab
end
```

</section>
Example
-------

This function lacks an example.

Author: NeonBlack

See Also
--------
