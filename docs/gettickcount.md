This function returns amount of time that your system has been running in milliseconds. By comparing two values of [getTickCount](/docs/gettickcount.md "wikilink"), you can determine how much time has passed (in milliseconds) between two events. This could be used to determine how efficient your code is, or to time how long a player takes to complete a task.

Syntax
------

``` lua
int getTickCount ()
```

### Returns

Returns an integer containing the number of milliseconds since the system the server is running on started. This has the potential to wrap-around.

Example
-------

This will start a timer displayed at the top of the screen displayed every frame. You can log any specific moment in time by outputting the currentCount variable.

    screenX,screenY = guiGetScreenSize()
    function startTheClock ()
        
        if not systemUpTime then
                systemUpTime = getTickCount () --Store the system tick count, this will be 0 for us
        end
        
        currentCount = getTickCount ()
        
        dxDrawRectangle (screenX *.40, screenY * .09, 250, 50, tocolor(0,0,0,150))
        dxDrawText ( currentCount - systemUpTime, screenX * .48, screenY * .1, screenX, screenY, tocolor(255,255,255), 2)
    end
    addEventHandler ( "onClientRender", root, startTheClock )

See Also
--------
