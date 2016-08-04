This function returns a percentage of a specific value.

Syntax
------

``` lua
float math.percent(float percent, float maxvalue)
```

### Required Arguments

-   **percent**: The percent you want to get.
-   **maxvalue**: The max value you want to get the percentage of.

Example
-------

<section name="Serverside script" class="server" show="true">
``` lua
function math.percent(percent,maxvalue)
    if tonumber(percent) and tonumber(maxvalue) then
        local x = (maxvalue*percent)/100
        return x
    end
    return false
end
```

</section>
This example returns 10% of 100.

``` lua
local n = math.percent(10,100)
print(n)
-- result will be 10, because 10% of 100 is 10.
```

Author: manawydan

See Also
--------
