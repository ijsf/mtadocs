This function is used to retrieve the current state of specified .

Syntax
------

``` lua
string ircGetBotState ( ircbot theBot )
```

### Required Arguments

-   **theBot:** The ircbot which current state you want to get

### Returns

Returns a string of the ircbot's current state. Possible values are:

-   **disconnected**
-   **connecting**
-   **connected**

If invalid arguments were passed, it returns *false*.

Example
-------

This example creates an ircbot called *DummyBot* and makes it connect to a server. During the connection progress bot's current states are printed out to the server log.

``` lua
function resourceStart ()
    dummyBot = ircCreateBot ( "DummyBot" )
    outputServerLog ( "DummyBot is now " .. ircGetBotState ( dummyBot ) ) -- "disconnected"
    ircConnect ( dummyBot, "irc.gtanet.com", 6667 )
    outputServerLog ( "DummyBot is now " .. ircGetBotState ( dummyBot ) ) -- "connecting"
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function event_ircOnConnect ( theBot )
    outputServerLog ( ircGetName ( theBot ) .. " is now " .. ircGetBotState ( theBot ) ) -- "connected"
end
```

See Also
--------
