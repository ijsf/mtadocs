Displays an message to an IRC Channel

Syntax
------

``` lua
function ircMessage ( IRCConnection irc, string channel, string message )
```

### Required arguments

-   **irc:** The IRCConnection
-   **channel:** The channel or person you want to send the message to
-   **message:** The message

Example
-------

**Example 1:** This echo is displaying all the ingame chat to \#mta with the IRCConnection stored in pIRC

``` lua

function ChatToIRC( message, type )
    if (type == 0) then -- Its an normal chatmessage
        ircMessage( pIRC, "#mta", "CHAT:�� " .. getClientName( source ) .. ": " .. message )
    elseif (type == 1) then -- Its an action
        ircMessage( pIRC, "#mta", "ACTION: " .. getClientName( source ) .. ": " .. message )
    elseif (type == 2) then -- Teamchat message
        ircMessage( pIRC, "#mta", "TEAMCHAT: " .. getClientName( source ) .. ": " .. message )
    end
end

addEventHandler( "onPlayerChat", getRootElement(), ChatToIRC )
```

See also
--------
