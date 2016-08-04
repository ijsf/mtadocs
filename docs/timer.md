A [timer](/docs/timer.md "wikilink") object refers to a timer set to execute a function a certain number of times with a specified delay.

Note that after a timer has completed all its iterations, it is destroyed and any stored pointers to it become invalid. Also timers are not under the *resource* hierarchy, because they are not elements, for instance, if you create a timer, it will not be destroyed when the resource in which it was created is stopped, so in this case you should kill the timer manually.

Related scripting functions
---------------------------

-   [getTimers](/docs/getTimers.md "wikilink")
-   [killTimer](/docs/killTimer.md "wikilink")
-   [setTimer](/docs/setTimer.md "wikilink")
-   [getTimerDetails](/docs/getTimerDetails.md "wikilink")
