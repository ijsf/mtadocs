This function can be used to join a channel. Note that a delay of 2-3 seconds should be used before calling this function inside callback .

Syntax
------

``` lua
bool ircJoinChannel ( ircbot theBot, string channel, [ string key = "" ] )
```

### Required Arguments

-   **theBot:** The ircbot which is going to join the channel
-   **channel:** The channel which the ircbot will connect to

### Optional Arguments

-   **key:** The key (password) for the channel. Needs to be specified for channels which have key set

### Returns

Returns *true* if passed arguments were valid, *false* otherwise.
**Note:** Does not return *true* if ircbot successfully joined or *false* if the bot failed to join the channel. You can check if the bot joined the channel by using callback .

Example
-------

This example creates an ircbot called *DummyBot* makes it connect to a server and join a channel called *\#testchannel* after it has connected.

``` lua
function resourceStart ( )
    theBot = ircCreateBot ( "DummyBot" )
    ircConnect ( theBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function event_ircOnConnect ( theBot )
    setTimer ( ircJoinChannel, 2000, 1, theBot, "#testchannel" )
end
```

See Also
--------
