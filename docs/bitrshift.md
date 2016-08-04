This functions performs a logical right shift on the integer **value** by integer **n** positions. In a *logical shift*, zeros are shifted in to replace the discarded bits. See [Bitwise operation](https://en.wikipedia.org/wiki/Bitwise_operation#Logical_shift) for more details.

Syntax
------

``` lua
int bitRShift ( int value, int n )
```

### Required arguments

-   **value:** The value you want to perform the shift on.
-   **n:** The amount of positions to shift the value by.

### Returns

Returns the logical right shifted value as *integer*.

Example
-------

This example shows the usage of the function [bitRShift](/docs/bitrshift.md "wikilink").

``` lua
local value = 0xFFFFFFFF -- binary: 1111 1111 1111 1111 1111 1111 1111 1111, decimal: 4.294.967.295
local positions = 0x4 -- binary: 0100, decimal: 4
local shifted = bitRShift( value, positions ) -- binary: 0000 1111 1111 1111 1111 1111 1111 1111, decimal: 26.8435.455

-- Comparsion:
-- binary: 1111 1111 1111 1111 1111 1111 1111 1111, decimal: 4.294.967.295
-- binary: 0000 1111 1111 1111 1111 1111 1111 1111, decimal: 26.8435.455
```

See Also
--------
