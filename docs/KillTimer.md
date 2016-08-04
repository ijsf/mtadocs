This function allows you to kill/halt existing timers.

Syntax
------

``` lua
bool killTimer ( timer theTimer )
```

### Required Arguments

-   **theTimer:** The [timer](/timer.md "wikilink") you wish to halt.

### Returns

Returns *true* if the timer was successfully killed, *false* if no such timer existed.

Example
-------

This example kills all timers with a remaining time of less than 1 minute.

``` lua
-- Find and kill all the timers with less than 1 minute to go
timers = getTimers ( 60000 )
-- Loop through the timer list
for timerKey, timerValue in ipairs(timers) do
    -- kill the timer
      killTimer ( timerValue )
end
```

This example checks if the time then kill the timer.

``` lua
-- set timer output text in chat box
local Timer = setTimer ( function ( ) outputChatBox ( 'Hello World !' ) end, 60000, 0 )
-- Check the timer then kill the timer
if isTimer ( Timer ) then killTimer ( Timer ) end
```

See Also
--------
