This function allows you to retrieve the color of a text item.

Syntax
------

``` lua
int int int int textItemGetColor ( textitem theTextItem )              
```

### Required Arguments

-   **theTextItem:** The text item you wish to retrieve the color of.

### Returns

Returns four integers in RGBA format, with a maximum value of 255 for each. The values are, in order, *red*, *green*, *blue*, and *alpha*. Alpha decides transparency where 255 is opaque and 0 is transparent. *false* is returned if the text item is invalid.

Example
-------

This example gets the color of a text item named 'theTextItem' and if it is green, changes it to blue.

``` lua
r,g,b,a = textItemGetColor ( theTextItem )           -- get the text color and store it in the variables 'r','g','b' and 'a'
if ( r == 0 ) and ( g == 255 ) and ( b == 0 ) then   -- if the color is green
    textItemSetColor ( theTextItem, 0, 0, 255, 255 ) -- set it to blue
end
```

See Also
--------
