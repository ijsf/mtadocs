This function can be used to part (leave) a channel. The specified has to be in the channel.

Syntax
------

``` lua
bool ircPartChannel ( ircbot theBot, [ string channel = "" ] )
```

### Required Arguments

-   **theBot:** The ircbot which is going to part the specified channel

### Optional Arguments

-   **channel:** The channel which the ircbot will part from. If not specified, parts the last joined channel

### Returns

Returns *true* if passed arguments were valid, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* makes it connect to a server and join a channel called *\#testchannel* after it has connected. It also makes it part that channel after a little while.

``` lua
function resourceStart ( )
    theBot = ircCreateBot ( "DummyBot" )
    ircConnect ( theBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function event_ircOnConnect ( theBot )
    setTimer ( ircJoinChannel, 2000, 1, theBot, "#testchannel" )
end

function event_ircOnJoinChannel ( theBot, channel, name )
    if name == ircGetName ( theBot ) then -- if the user which connected was the ircbot
        setTimer ( ircPartChannel, 5000, 1, theBot, channel )
    end
end
```

See Also
--------
