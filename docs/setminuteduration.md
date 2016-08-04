Sets the real-world duration of an ingame minute. The GTA default is 1000.

Syntax
------

``` lua
bool setMinuteDuration ( int milliseconds )
```

### Required Arguments

-   **milliseconds**: the new duration of an ingame minute

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

This example will make the ingame time correspond to the real-world time of the server.

<section class="server" name="Server" show="true">
``` lua
function resourceStart()
    local realtime = getRealTime()

    setTime(realtime.hour, realtime.minute)
    setMinuteDuration(60000)
end
addEventHandler("onResourceStart", getResourceRootElement(), resourceStart)
```

</section>
See Also
--------

[ru:setMinuteDuration](/docs/ru-setminuteduration.md "wikilink")
