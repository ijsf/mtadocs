Syntax
------

``` lua
uint bitExtract ( uint var, int field [, int width = 1 ] )
```

### Required arguments

-   **var:** The value
-   **field:** The field number
-   **width:** Number of bits to extract

### Returns

Returns the extracted value/bit sequence.

Example
-------

``` lua
function getColorAlpha(color)
   return bitExtract(color,24,8) -- return bits 24-32 ( the alpha, http://en.wikipedia.org/wiki/RGBA_color_space ) 
end
```

See Also
--------
