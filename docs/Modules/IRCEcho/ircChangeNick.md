Changes the name of the IRCConnection

Syntax
------

``` lua
function ircChangeNick ( IRCConnection irc, string newnick )
```

### Required arguments

-   **irc:** The IRCConnection
-   **newnick:** The new nickname

Example
-------

**Example 1:** This example adds the command “ircname”. That command can change the IRCConnection's name

``` lua

function changeIrcName( thePlayer, command, newname )
    ircChangeNick( pIRC, newname )
end

addCommandHandler( "ircname", changeIrcName )
```

See also
--------
