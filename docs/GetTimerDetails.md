This function is for getting the details of a running timer.

Syntax
------

``` lua
int, int, int getTimerDetails ( timer theTimer )
```

### Required Arguments

-   **theTimer:** A timer element.

### Returns

-   Integer one represents the time left in miliseconds (1000th of a second) of the current time left in the loop.
-   Integer two represents the amount of times the timer has left to execute.
-   Integer three represents the amount of times the timer will execute.

<!-- -->

-   Returns false if the timer doesn't exist or stopped running. Also, debugscript will say “Bad Argument @ 'getTimerDetails'”. To prevent this, you can check if the timer exists with [isTimer](/isTimer.md "wikilink")().

Example
-------

This example creates a 1 second (1000 ms) timer that will run 1000 times, and you can see the timer details by using the command: timerdetails.

``` lua
theTimer = setTimer(function() end, 1000, 10) -- A timer that does nothing.

function timerDetails()
    remaining, executesRemaining, totalExecutes = getTimerDetails(theTimer) -- Get the timers details
    if (remaining and executesRemaining and totalExecutes) then
        outputChatBox("Time remaining this second: "..remaining.." Executes remaining: "..executesRemaining.." Total executes: "..totalExecutes)
    else
        outputChatBox("Timer no longer exists")
    end
end
addCommandHandler("timerdetails", timerDetails)
```

See Also
--------
