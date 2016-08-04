This function is used to disconnect an from a server.

Syntax
------

``` lua
bool ircQuit ( ircbot theBot, [ string quitMessage ] )
```

### Required Arguments

-   **theBot:** The ircbot which will be disconnected.

### Optional Arguments

-   **quitMessage:** A quit message to be displayed when quitting. By default it uses the quit message set by .

### Returns

Returns *true* if passed arguments were valid, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* and makes it connect to irc.gtanet.com server on resource start. When the resource stops, the bot is also disconnected from the server and destroyed.

``` lua
function resourceStart()
    theBot = ircCreateBot ( "DummyBot" )
    ircConnect ( theBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function resourceStop()
    if theBot then
        ircQuit ( theBot )
        ircDestroyBot ( theBot )
    end
end
addEventHandler ( "onResourceStop", getResourceRootElement ( getThisResource() ), resourceStop )
```

See Also
--------
