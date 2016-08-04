Syntax
------

``` lua
uint bitAnd ( uint var1, uint var2, ... )
```

### Required arguments

-   **varN:** The value you want to perform an AND-conjunction on

### Returns

Returns the conjuncted value.

Example
-------

``` lua
local flags = 0x23 -- binary: 100011b
local mask = 0x20  -- binary: 100000b

-- Check if bit 1 is set
if bitAnd(flags, mask) ~= 0 then
    outputDebugString"Yeah. It's set"
else
    outputDebugString"I'm sorry ;("
end
```

To test if a flag is set or not it's easier using [bitTest](/docs/bittest.md "wikilink").

See Also
--------
