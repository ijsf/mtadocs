This function allows you to trigger a function after a number of milliseconds have elapsed. You can call one of your own functions or a built-in function. For example, you could set a timer to spawn a player after a number of seconds have elapsed.

Once a timer has finished repeating, it no longer exists.

**The minimum accepted interval is 50ms.**

Multi Theft Auto guarantees that the timer will be triggered after *at least* the interval you specify. The resolution of the timer is tied to the frame rate (server side and client-side). All the overdue timers are triggered at a single point each frame. This means that if, for example, the player is running at 30 frames per second, then two timers specified to occur after 100ms and 110ms would more than likely occur during the same frame, as the difference in time between the two timers (10ms) is less than half the length of the frame (33ms). As with most timers provided by other languages, you shouldn't rely on the timer triggering at an exact point in the future.

Syntax
------

``` lua
timer setTimer ( function theFunction, int timeInterval, int timesToExecute, [ var arguments... ] )
```

### Required Arguments

-   **theFunction:** The function you wish the timer to call. (Notice: Do not use a 'local' function, it must be global!)

-   **timeInterval:** The number of milliseconds that should elapse before the function is called. (the minimum is 50; 1000 milliseconds = 1 second)
-   **timesToExecute:** The number of times you want the timer to execute, or 0 for infinite repetitions.

### Optional Arguments

-   **arguments:** Any arguments you wish to pass to the function can be listed after the *timesToExecute* argument. Note that any tables you want to pass will get cloned, whereas metatables and functions/function references in that passed table will get lost. Also changes you make in the original table before the function gets called won't get transferred.

### Returns

Returns a [timer](/timer.md "wikilink") pointer if the timer was set successfully, *false* if the arguments are invalid or the timer could not be set.

Examples
--------

This example will output some text after a small delay.

``` lua
-- define function to be called
function delayedChat ( text )
    outputChatBox ( "Delayed text: " .. text )
end

-- set a timer so the function is called after 1 second
setTimer ( delayedChat, 1000, 1, "Hello, World!" )
```

1 second after the line above has been executed, the text *Delayed text: Hello, World!* will be displayed in the chat box.

This example will nest a whole function within a timer. This is nice for things like setting variables without having to call a function outside of your code block.

``` lua
function mainFunction()
        outputChatBox ("Instant text!")
    setTimer ( function()
        outputChatBox ( "5 second delay text!" )
    end, 5000, 1 )
end

mainFunction() --call function
```

This example outputs some random text to the chat every 300000 milliseconds (5 minutes).

``` lua
setTimer(
function()
    outputChatBox("Text " .. math.random(1,4))
end, 300000, 0)
```

See Also
--------
