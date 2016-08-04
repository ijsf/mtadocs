<lowercasetitle></lowercasetitle>

This function maths the age of the given birthday.

Syntax
------

``` lua
int getAge(int day, int month, int year)
```

### Required Arguments

-   **day**: The day when the player was born.
-   **month**: The month when the player was born.
-   **year**: The year when the player was born.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getAge(day, month, year)
    local time = getRealTime();
    time.year = time.year + 1900;
    time.month = time.month + 1;
    
    year = time.year - year;
    month = time.month - month;
    
    if month < 0 then 
        year = year - 1 
    elseif month == 0 then
        if time.monthday < day then
            year = year - 1;
        end
    end
    
    return year;
end
```

</section>
Example
-------

<section name="Example" class="both" show="true">
``` lua
-- A simple example:
addEventHandler("onResourceStart", getRootElement(), function()
    print(getAge(09, 04, 1989))
end);
-- that will output:
-- 20
-- Yep, i'm 20 years old!
```

</section>
Function created by **Alexander de Jong AKA mrdejong**.

See Also
--------

[pl:GetAge](/docs/pl-getage.md "wikilink")
