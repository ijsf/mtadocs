Syntax
------

``` lua
uint bitReplace ( uint var, uint replaceValue, int field, int width = 1 )
```

### Required arguments

-   **var:** The value
-   **replaceValue:** The replaceValue
-   **field:** The field number
-   **width:** Number of bits to extract

### Returns

Returns the replaced value/bit sequence.

Example
-------

``` lua
function replaceColorAlpha(color, alpha)
   return bitReplace(color,alpha,24,8) -- return value with replaced bits 24-32 ( the alpha, http://en.wikipedia.org/wiki/RGBA_color_space ) 
end
```

See Also
--------
