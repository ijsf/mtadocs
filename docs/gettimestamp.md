With this function you can get the [UNIX timestamp](http://en.wikipedia.org/wiki/Unix_time).

Syntax
------

``` lua
 )
```

### Optional Arguments

-   **year**: The year of the date you want to retrieve the UNIX timestamp of. Default is your local year. Must be greater than 1969.
-   **month**: The month of the date you want to retrieve the UNIX timestamp of. Default is your local month. (1-12)
-   **day**: The day of the date you want to retrieve the UNIX timestamp of. Default is your local day. (1-31)
-   **hour**: The hour of the date you want to retrieve the UNIX timestamp of. Default is your local hour. (0-23)
-   **minute**: The minute of the date you want to retrieve the UNIX timestamp of. Default is your local minute. (0-59)
-   **second**: The second of the date you want to retrieve the UNIX timestamp of. Default is your local second. (0-59)

### Returns

Returns an UNIX timestamp.

Code
----

<section name="Client- and/or serverside Script" class="both" show="true">
``` lua
function getTimestamp(year, month, day, hour, minute, second)
    -- initiate variables
    local monthseconds = { 2678400, 2419200, 2678400, 2592000, 2678400, 2592000, 2678400, 2678400, 2592000, 2678400, 2592000, 2678400 }
    local timestamp = 0
    local datetime = getRealTime()
    year, month, day = year or datetime.year + 1900, month or datetime.month + 1, day or datetime.monthday
    hour, minute, second = hour or datetime.hour, minute or datetime.minute, second or datetime.second
    
    -- calculate timestamp
    for i=1970, year-1 do timestamp = timestamp + (isLeapYear(i) and 31622400 or 31536000) end
    for i=1, month-1 do timestamp = timestamp + ((isLeapYear(year) and i == 2) and 2505600 or monthseconds[i]) end
    timestamp = timestamp + 86400 * (day - 1) + 3600 * hour + 60 * minute + second
    
    timestamp = timestamp - 3600 --GMT+1 compensation
    if datetime.isdst then timestamp = timestamp - 3600 end
    
    return timestamp
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example saves the time of the player's joining.

``` lua
-- define the event handler
addEventHandler("onPlayerJoin", root, function ()
    -- get the actual UNIX timestamp
    local datetime = getTimestamp()
    -- attach the time to the player's element
    setElementData(source, "joinTime", datetime)
end)
```

</section>
Author: NeonBlack

See Also
--------
