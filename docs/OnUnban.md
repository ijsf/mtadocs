This event is triggered when a ban is removed from the server.

if the ban was removed using function [removeBan](/removeBan.md "wikilink"), and the responsibleElement was not specifying, the event will return nil.

Parameters
----------

``` lua
ban theBan, player responsibleElement
```

-   '''theBan ''': The [ban](/ban.md "wikilink") that will be removed.
-   **responsibleElement**: The player who removed the ban, otherwise return nil.

Source
------

The source is always the global root element.

Cancel effect
-------------

If this event is [canceled](/Event_system#Canceling.md "wikilink"), the requested unban is not performed.

Example
-------

This example does...

``` lua
root = getRootElement()

function announceUnban( theBan, responsibleElement )
    if getElementType( responsibleElement ) then --Check if a player unbanned the IP/Serial
        outputChatBox( getPlayerName( responsibleElement ) .. " unbanned " .. ( getBanSerial(theBan) or getBanIP(theBan) ) ) --Output to the chatbox saying the player has unbanned the IP/Serial
    end
end

addEventHandler( "onUnban", root, announceUnban ) --Adds the event handler for 'onUnban'
```

Changelog
---------
