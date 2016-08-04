This functions performs a logical left shift on the integer **value** by integer **n** positions. In a *logical shift*, zeros are shifted in to replace the discarded bits. See [Bitwise operation](https://en.wikipedia.org/wiki/Bitwise_operation#Logical_shift) for more details.

Syntax
------

``` lua
int bitLShift ( int value, int n )
```

### Required arguments

-   **value:** The value you want to perform the shift on.
-   **n:** The amount of positions to shift the value by.

### Returns

Returns the logical left shifted value as *integer*.

Example
-------

This example shows the usage of the function [bitLShift](/docs/bitlshift.md "wikilink").

``` lua
local value = 0xFFFFFFFF -- binary: 1111 1111 1111 1111 1111 1111 1111 1111, decimal: 4.294.967.295
local positions = 0x4 -- binary: 0100, decimal: 4
local shifted = bitLShift( value, positions ) -- binary: 1111 1111 1111 1111 1111 1111 1111 0000, decimal: 4.294.967.280

-- Comparsion:
-- binary: 1111 1111 1111 1111 1111 1111 1111 1111, decimal: 4.294.967.295
-- binary: 1111 1111 1111 1111 1111 1111 1111 0000, decimal: 4.294.967.280
```

See Also
--------
