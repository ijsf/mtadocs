<lowercasetitle></lowercasetitle>

This function check is empty table or not.

Syntax
------

``` lua
boolean table.empty( table a )
```

### Required Arguments

-   **a**: The table for check.

### Returns

Returns the true if table is empty or false in otherwise.

<section name="Code" class="both" show="true">
``` lua
function table.empty( a )
    if type( a ) ~= "table" then
        return false
    end
    
    return not next( a )
end
```

</section>
<section name="Example" class="both" show="true">
``` lua
print( 'empty = ' .. tostring( table.empty( { [0] = 1 } ) ) ) -- false
print( 'empty = ' .. tostring( table.empty( { [10] = 10, [2] = 2 } ) ) ) -- false
print( 'empty = ' .. tostring( table.empty( { } ) ) ) -- true
```

</section>
Author: Kenix

See Also
--------
