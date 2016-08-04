This function returns the hypotenuse of the right-angled triangle given by two legs (catheti), which are the sides adjacent to the right angle.

Syntax
------

``` lua
float math.hypot( float legX, float legY )
```

### Required arguments

-   **legX**: Triangle's first leg.
-   **legY**: Triangle's second leg.

Code
----

``` lua
function math.hypot( legX, legY )
    -- Pythagorean theorem
    return ((legX ^ 2) + (legY ^ 2)) ^ .5
end
```

**Author**: CiBeR

Example
-------

This example gets the hypotenuse of a triangle whose legs are 3 and 4.

``` lua
local h = math.hypot(3, 4)
print(h)
-- This prints 5.0
```

See also
--------
