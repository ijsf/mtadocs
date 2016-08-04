This functions performs a bitwise circular left-rotation on the integer **value** by integer **n** positions. See [Bitwise operation](https://en.wikipedia.org/wiki/Bitwise_operation#Rotate_no_carry) for more details.

Syntax
------

``` lua
int bitLRotate ( int value, int n )
```

### Required arguments

-   **value:** The value you want to perform the rotation on.
-   **n:** The amount of positions to rotate the value by.

### Returns

Returns the circular left-rotated value as *integer*.

Example
-------

This example shows the usage of the function [bitLRotate](/docs/bitlrotate.md "wikilink").

``` lua
local value = 0xF -- binary: 1111, decimal: 15
local positions = 0x1 -- binary: 0001, decimal: 1
local shifted = bitLRotate( value, positions ) -- binary: 0001 1110, decimal: 30

local value = 0xF -- binary: 1111, decimal: 15
local positions = 0x3 -- binary: 0011, decimal: 3
local shifted = bitLRotate( value, positions ) -- binary: 0111 1000, decimal: 120

local value = 0x3F -- binary: 0011 1111, decimal: 63
local positions = 0xA -- binary: 1010, decimal: 10
local shifted = bitLRotate( value, positions ) -- binary: 1111 1100 0000 0000, decimal: 64.512
```

See Also
--------
