This function is used to get the current time in the game. If you want to get the real server time, use [getRealTime](/docs/getrealtime.md "wikilink").

Syntax
------

``` lua
int int getTime ()
```

### Returns

Returns two *ints* that represent hours and minutes.

Example
-------

These two examples adds the command *gettime* which outputs the local game time and the server game time.

<section name="Client" class="client" show="true">
``` lua
function currentTime()
    local hour, minutes = getTime()
    outputChatBox( "The current game time is "..hour..":"..minutes )
end
addCommandHandler("gettime", currentTime)
```

</section>
<section name="Server" class="server" show="true">
``` lua
function currentTime(sourcePlayer)
    local hour, minutes = getTime()
    outputChatBox( "The current game time (server) is "..hour..":"..minutes, sourcePlayer )
end
addCommandHandler("gettime", currentTime)
```

</section>
See Also
--------

[ru:getTime](/docs/ru-gettime.md "wikilink")
