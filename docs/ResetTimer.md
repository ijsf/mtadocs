This function allows you to reset the elapsed time in existing timers to zero. The function does not reset the 'times to execute' count on timers which have a limited amout of repetitions.

Syntax
------

``` lua
bool resetTimer ( timer theTimer )
```

### Required Arguments

-   **theTimer:** The [timer](/docs/timer.md "wikilink") whose elapsed time you wish to reset.

### Returns

Returns *true* if the timer was successfully reset, *false* otherwise.

Example
-------

``` lua
local timer = setTimer(example,3000,1)

function example()
   outputChatBox("3 seconds has passed.")
   resetTimer(timer)
end
```

See Also
--------
