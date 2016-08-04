This function returns a table of all active timers that the resource that calls it has created. Alternatively, only the timers with a remaining time less than or equal to a certain value can be retrieved.

Syntax
------

``` lua
table getTimers ( [ theTime = nil ] )
```

### Optional Arguments

-   **theTime:** The maximum time left (in milliseconds) on the timers you wish to retrieve.

### Returns

Returns a table of all the active timers.

Example
-------

This example kills timers with a remaining time of less than 1 minute.

``` lua
-- Find and kill all the timers with less than 1 minute to go
timers = getTimers ( 60000 )
-- Loop through the timer list
for timerKey, timerValue in ipairs(timers) do
    -- kill the timer
      killTimer ( timerValue )
end
```

See Also
--------
