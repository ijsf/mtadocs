This function gets the server or client (if used client sided it returns time as set on client's computer) real time and returns it in a table. If you want to get the in-game time (shown on GTA's clock) use [getTime](/getTime.md "wikilink").

Syntax
------

``` lua
 )
```

### Optional Arguments

-   **seconds:** A count in seconds from the year 1970. Useful for storing points in time, or for retrieving time information for [getBanTime](/getBanTime.md "wikilink"). The valid range of this argument is 0 to 32,000,000,000

### Returns

Returns a *table* of substrings with different time format or *false* if the **seconds** argument is out of range.

|            |                                            |           |
|------------|--------------------------------------------|-----------|
| **Member** | **Meaning**                                | **Range** |
| second     | seconds after the minute                   | 0-61\*    |
| minute     | minutes after the hour                     | 0-59      |
| hour       | hours since midnight                       | 0-23      |
| monthday   | day of the month                           | 1-31      |
| month      | months since January                       | 0-11      |
| year       | years since 1900                           |
| weekday    | days since Sunday                          | 0-6       |
| yearday    | days since January 1                       | 0-365     |
| isdst      | Daylight Saving Time flag                  |
| timestamp  | seconds since 1970 (Ignoring set timezone) |           |

-   *second* is generally 0-59. Extra range to accommodate for leap seconds in certain systems.

Example
-------

This example outputs local time (server or client, where ever it was triggered) as hours and minutes

``` lua
function showtime ()
    local time = getRealTime()
    local hours = time.hour
    local minutes = time.minute
    outputChatBox ( "Local Time: "..hours..":"..minutes )
end
```

Changelog
---------

See Also
--------

[ru:getRealTime](/ru:getRealTime.md "wikilink")
