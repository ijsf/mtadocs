Syntax
------

``` lua
uint bitXor ( uint var1, uint var2, ... )
```

### Required arguments

-   **varN:** The value you want to perform a XOR-conjunction on

### Returns

Returns the conjuncted value.

Example
-------

This example will do a bitwise XOR of x1, x2, ...

``` lua
local x1 = 0x14 -- binary: 0001 0100
local x2 = 0x1C -- binary: 0001 1100

bitXor(x1, x2)  -- return  0000 1000
```

See Also
--------
