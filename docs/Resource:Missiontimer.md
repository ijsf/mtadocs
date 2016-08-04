Missiontimer is a resource used to easily create timers that count down or up in your resources.

Overview
--------

The “deathmatch” gamemode is an example use of missiontimer. It uses the “createMissionTimer” function to create a timer, and then the onMissionTimerElapsed event to trigger at the end:

``` lua
    g_MissionTimer = exports.missiontimer:createMissionTimer (g_TimeLimit,true,"%m:%s",0.5,20,true,"default-bold",1,255,255,255)
    addEventHandler ( "onMissionTimerElapsed", g_MissionTimer, onTimeElapsed )
 
```

Then you use the onTimeElapsed function that you attached to the handler at the end of the timer.

The arguments for createMissionTimer as follows:

``` lua
createMissionTimer ( duration, countdown, format, x, y, bg, font, scale, r, g, b )
```

-   duration - The time in milliseconds
-   countdown - A bool of whether to countdown or count up. Setting it to true will count down from the duration, setting it to false will count up to the duration (latter isnt tested yet)
-   format - A string detailing the format of the timer text to be shown. You can chose whether to show minutes, seconds or centiseconds using these 3 strings:
    -   %m - minutes
    -   %s - seconds
    -   %cs - centiseconds

This allows you to add normal text onto the timer as well as showing the time left (eg: “Time left: %m:%s”)

-   x,y - Position on the screen, this uses “smart positioning”. It can be relative or absolute - the deathmatch gamemode creates it at 0.5,20. This means the x value is in the centre, the y is 20pixels from the top. If you specify a negative value it draws the other way, i.e. -20 would be 20pixels from the bottom rather than the top. The same can be done for x.
-   bg - Whether to draw the default rounded-rectangle behind the timer. Setting this to false will hide it
-   font - The font of the timer. Looks best in default-bold
-   scale - The size of the text/bg.
-   r,g,b - The red/green/blue components to make up the colour of the timer text (defaults to white)

There are also some other exported functions that you may or may not need:

``` lua
setMissionTimerTime ( missionTimer, time )
```

Sets the countdown/countup target time (in milliseconds)

``` lua
getMissionTimerTime ( missionTimer )
```

Gets the number currently showing on the clock (in milliseconds)

``` lua
setMissionTimerFrozen ( missionTimer, frozen )
```

Sets the timer to frozen (true) or normal (false)

``` lua
isMissionTimerFrozen ( missionTimer )
```

See if the timer is frozen

``` lua
setMissionTimerHurryTime ( missionTimer, time )
```

Set the time that the clock will turn red (in milliseconds) (ie: to indicate there is not much time left)

``` lua
setMissionTimerFormat ( missionTimer, format )
```

Set the text format for the timer

To remove a missiontimer from the screen, use [destroyElement](/destroyElement.md "wikilink").

Missiontimer is only compatible with MTASA 1.0 onwards.

[ru:<Resource:Missiontimer>](/ru:Resource:Missiontimer.md "wikilink")
