<lowercasetitle></lowercasetitle>

This function checks, whether vehicle is laying on roof.

Syntax
------

``` lua
bool isVehicleOnRoof(vehicle vehicle)
```

### Required Arguments

-   **vehicle**: Vehicle element.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function isVehicleOnRoof(vehicle)
        local rx,ry=getElementRotation(vehicle)
        if (rx>90 and rx<270) or (ry>90 and ry<270) then
                return true
        end
        return false
end
```

</section>
See Also
--------
