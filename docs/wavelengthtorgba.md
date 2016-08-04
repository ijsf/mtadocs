<lowercasetitle></lowercasetitle>

This function retrieves the RGBA components of a wavelenght.

Syntax
------

``` lua
int, int, int, int wavelengthToRGBA ( int length )
```

### Required Arguments

-   **length :** The wavelength of the light in nanometers.

### Returns

Returns four color components in RGBA format.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function wavelengthToRGBA (length)
    local r, g, b, factor
    if (length >= 380 and length < 440) then
        r, g, b = -(length - 440)/(440 - 380), 0, 1
    elseif (length < 489) then
        r, g, b = 0, (length - 440)/(490 - 440), 1
    elseif (length < 510) then
        r, g, b = 0, 1, -(length - 510)/(510 - 490)
    elseif (length < 580) then
        r, g, b = (length - 510)/(580 - 510), 1, 0
    elseif (length < 645) then
        r, g, b = 1, -(length - 645)/(645 - 580), 0
    elseif (length < 780) then
        r, g, b = 1, 0, 0
    else
        r, g, b = 0, 0, 0
    end
    if (length >= 380 and length < 420) then
        factor = 0.3 + 0.7*(length - 380)/(420 - 380)
    elseif (length < 701) then
        factor = 1
    elseif (length < 780) then
        factor = 0.3 + 0.7*(780 - length)/(780 - 700)
    else
        factor = 0
    end
    return r*255, g*255, b*255, factor*255
end
```

</section>
Author: Lex128

See Also
--------
