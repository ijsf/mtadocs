Lets the IRCConnection leave a channel

Syntax
------

``` lua
function ircPart ( IRCConnection irc, string channel )
```

### Required arguments

-   **irc:** The IRCConnection
-   **channel:** The channel you want to leave

Example
-------

**Example 1:** This command makes the bot leave a channel

``` lua

function ircLeaveChannel( thePlayer, command, channel )
    ircPart( pIRC, channel )
end

addCommandHandler( "ircpart", ircLeaveChannel )
```

See also
--------
