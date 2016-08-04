Syntax
------

``` lua
uint bitOr ( uint var1, uint var2, ... )
```

### Required arguments

-   **varN:** The value you want to perform an OR-conjunction on

### Returns

Returns the conjuncted value.

Example
-------

This example will do a bitwise OR of x1, x2, ...

``` lua
local x1 = 0x31 -- binary: 0011 0001
local x2 = 0x19 -- binary: 0001 1001

bitOr(x1, x2)   -- return  0011 1001
```

See Also
--------
