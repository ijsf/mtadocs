Lets the IRCConnection join an channel

Syntax
------

``` lua
function ircJoin ( IRCConnection irc, string channel )
```

### Required arguments

-   **irc:** The IRCConnection
-   **channel:** The channel you want to join

Example
-------

**Example 1:** This command makes the bot join another channel

``` lua

function ircJoinChannel( thePlayer, command, channel )
    ircJoinChannel( pIRC, channel )
end

addCommandHandler( "ircjoin", ircJoinChannel )
```

See also
--------
