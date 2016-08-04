Notice somebody of an action

Syntax
------

``` lua
function ircNotice ( IRCConnection irc, string channel, string message )
```

### Required arguments

-   **irc:** The IRCConnection
-   **channel:** The channel or user you want to send to
-   **message:** The message

Example
-------

**Example 1:** This example is warning IJs of an banned user

``` lua

function ReportBan( ip )
    ircNotice( pIRC, "IJs", getPlayerName( source ) .. " banned " .. sz )
end

addEventHandler( "onBan", getRootElement(), ReportBan )
```

See also
--------
