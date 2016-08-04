Sends an raw message to the IRCConnection

Syntax
------

``` lua
function ircRaw ( IRCConnection irc, string command )
```

### Required arguments

-   **irc:** The IRCConnection
-   **command:** The command that you want to send to the IRC server

Example
-------

**Example 1:** This makes the IRCConnection ban Fedor!\*@\*

``` lua

function ircBanHost( thePlayer, command, channel )
    ircRaw("MODE #mta +B Fedor!*@*")
end

addCommandHandler( "disgrace", ircBanHost )
```

See also
--------
