Syntax
------

``` lua
bool bitTest ( uint var1, uint var2, ... )
```

### Required arguments

-   **varN:** The value you want to perform the operation on (see above)

### Returns

Returns *true* if the conjuncted value is **not** zero, *false* otherwise. If a bad argument was passed to [bitTest](/docs/bittest.md "wikilink"), you'll get *nil*.

Example
-------

``` lua
local flags = 0x23 -- binary: 100011b
local mask = 0x20  -- binary: 100000b

-- Check if bit 1 is set
if bitTest(flags, mask) then
    outputDebugString("Yeah. It's set")
else
    outputDebugString("I'm sorry ;(")
end
```

See Also
--------
