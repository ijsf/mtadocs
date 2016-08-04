This function is used to connect an created with to a server.
**Note:** The maximum number of simultanuous connections is 5. There is no limit for ircbots but it is not possible to connect more than 5 bots at a time.

Syntax
------

``` lua
bool ircConnect ( ircbot theBot, string server, int port, [ string password ] )
```

### Required Arguments

-   **theBot:** The ircbot which will be connected.
-   **server:** The name of the server to which the bot will connect, eg. “irc.gtanet.com”.
-   **port:** The port number of the IRC server.

### Optional Arguments

-   **password:** The password for the IRC server.

### Returns

Returns *true* if passed arguments were valid, *false* otherwise.
**Note:** Does not return *true* if ircbot was successfully connected or *false* if the bot didn't connect. You can check if the bot connected by using callbacks and .

Example
-------

This example creates an ircbot called *DummyBot* and makes it connect to irc.gtanet.com server on resource start.

``` lua
function resourceStart()
    theBot = ircCreateBot ( "DummyBot" )
    ircConnect ( theBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement (), resourceStart )
```

See Also
--------
