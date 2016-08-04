This function checks if a year is a leap year or not.

Syntax
------

``` lua
 )
```

### Optional Arguments

-   **year**: The year you want to check. Default is your local year.

### Returns

Returns *true* if the year is a leap year, *false* otherwise.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function isLeapYear(year)
    if year then year = math.floor(year)
    else year = getRealTime().year + 1900 end
    return ((year % 4 == 0 and year % 100 ~= 0) or year % 400 == 0)
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example tells the player if the given year is a leap year.

``` lua
-- define the command handler
addCommandHandler("isYearALeapYear", function (source, cmd, year)
    -- check if the player passed a year
    year = tonumber(year) or getRealTime().year + 1900
    -- check if the given year is a leap year
    local leapYear = IsYearALeapYear(year)
    --send an answer to the player
    if leapYear then
        outputChatBox("The year "..year.." is a leap year.", source)
    else
        outputChatBox("The year "..year.." isn't a leap year.", source)
    end
end, false, false)
```

</section>
Author: NeonBlack

See Also
--------
