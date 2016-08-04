This event is triggered when an IP address or serial is banned from the server.

Parameters
----------

``` lua
ban theBan
```

-   '''theBan ''': The [ban](/docs/ban.md "wikilink") which was added.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [element](/docs/element.md "wikilink") that was responsible for the banning. If no responsible was specified, the source is the global root element.

Cancel effect
-------------

This event cannot be canceled.

Example
-------

This example outputs a simple message to all players when a player added a ban.

``` lua
function announceBan( theBan )
    if getElementType( source ) then --Check if a player banned the IP/Serial
        outputChatBox( getPlayerName( source ) .. " banned " .. ( getBanSerial(theBan) or getBanIP(theBan) ) ) --Output to the chatbox saying the player has banned the IP/Serial
    end
end

addEventHandler( "onBan", root, announceBan ) --Adds the event handler for 'onBan' and must be bound to root
```
