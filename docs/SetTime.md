This function sets the current GTA time to the given time.

Syntax
------

``` lua
bool setTime ( int hour, int minute )
```

### Required Arguments

-   **hour**: The hour of the new time (range 0-23).
-   **minute**: The minute of the new time (range 0-59).

Returns
-------

Returns *true* if the new time was successfully set, *false* otherwise.

Example
-------

<section name="Example 1" class="server" show="true">
This serverside function sets the time and notifies players.

``` lua
function setTimeAndNotify( hour, minute )
    -- set the time first
    setTime ( hour, minute )
    -- format a notification message, adding leading zeros (e.g. 12:03 instead of 12:3)
    local notifyMessage = string.format("Time changed to %02d:%02d!", hour, minute)
    -- output the message
    outputChatBox ( notifyMessage )
end
```

</section>
<section name="Example 2" class="client" show="true">
This example freeze the time.

``` lua
addEventHandler( 'onClientRender', getRootElement( ),
    function( )
        setTime( 1, 0 )
    end
)
```

</section>
See Also
--------

[ru:setTime](/docs/ru:setTime.md "wikilink")
