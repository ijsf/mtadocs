This function calculates the easter date of a given year.

Syntax
------

``` lua
int int getEasterDate( int year )
```

### Required Arguments

-   **year**: The year of which the date will be calculated.

### Returns

Returns two integers representing the monthday and the month of the easter date.

Code
----

``` lua
function getEasterDate(year)
    local y = tonumber(year)
    assert(y, "Bad argument 1 @ getEasterDate [Number expected, got " .. type(year) .. "]")

    local M = 24
    local N = 5
    local a = y%19
    local b = y%4

    local c = y%7 
    local d = (19*a+M)%30 
    local e = (2*b+4*c+6*d+N)%7 
    local dayMar = 22+d+e
    local dayApr = d+e-9

    if dayMar > 31 then
        return dayApr, 4
    else
        return dayMar, 3
    end
end
```

Example
-------

<section name="Clientside script" class="client" show="true">
This example calculates the easter date of a given year with a command.

``` lua
addCommandHandler("easter",function(_, year)
    local day, month = getEaster(year) 
    outputChatBox("Easter "..year..": "..day.."/"..month)
end)
```

</section>
See also
--------
