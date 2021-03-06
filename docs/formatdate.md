This function formats a date according to the given format string.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **theFormat**: Format string that determines how the date should be formatted. It provides the following wildcards:
    -   d: day (01-31)
    -   h: hour (00-23)
    -   i: minute (00-59)
    -   m: month (01-12)
    -   s: second (00-59)
    -   w: shortened day of the week (Su-Mo)
    -   W: day of the week (Sunday-Monday)
    -   y: shortened year (e.g. 09)
    -   Y: year (e.g. 2009)

### Optional Arguments

-   **escaper**: Escape character that determines the beginning or end of a non-format-area, where the wildcards aren't replaced with their corresponding value. Note that the escapers get lost.
-   **timestamp**: Timestamp of the date that should be formatted.

### Returns

Returns a string containing the formatted date.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
local gWeekDays = { "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday" }
function FormatDate(format, escaper, timestamp)
    Check("FormatDate", "string", format, "format", {"nil","string"}, escaper, "escaper", {"nil","string"}, timestamp, "timestamp")
    
    escaper = (escaper or "'"):sub(1, 1)
    local time = getRealTime(timestamp)
    local formattedDate = ""
    local escaped = false

    time.year = time.year + 1900
    time.month = time.month + 1
    
    local datetime = { d = ("%02d"):format(time.monthday), h = ("%02d"):format(time.hour), i = ("%02d"):format(time.minute), m = ("%02d"):format(time.month), s = ("%02d"):format(time.second), w = gWeekDays[time.weekday+1]:sub(1, 2), W = gWeekDays[time.weekday+1], y = tostring(time.year):sub(-2), Y = time.year }
    
    for char in format:gmatch(".") do
        if (char == escaper) then escaped = not escaped
        else formattedDate = formattedDate..(not escaped and datetime[char] or char) end
    end
    
    return formattedDate
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example outputs the actual date to a joining player.

``` lua
-- get the root element
local _root = getRootElement()
-- define the onPlayerJoin handler function
function OnPlayerJoin()
    -- output the formatted date
    outputChatBox(FormatDate("'You joined our server on' m/d/Y at h:m."))
end
-- add the event handler
addEventHandler("onPlayerJoin", _root, OnPlayerJoin)
```

</section>
Author: NeonBlack

See Also
--------
