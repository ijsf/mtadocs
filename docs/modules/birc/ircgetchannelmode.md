This function returns the current channel mode of the specified channel. The specified has to be in that channel.

Syntax
------

``` lua
string ircGetChannelMode ( ircbot theBot, string channel )
```

### Required Arguments

-   **theBot:** The ircbot which is in the channel
-   **channel:** The name of the channel which channel mode you want to get

### Returns

Returns the currently set [channel mode](http://www.alien.net.au/irc/chanmodes.html) (letters) or an empty string if there is no modes set in that channel.

Example
-------

This example creates an ircbot called *DummyBot* makes it connect to a server and join a channel. It also includes an IRC command '!istopiclocked' which can used to check if the topic is locked (only channel ops can change it) on that channel.

``` lua
function resourceStart ( )
    theBot = ircCreateBot ( "DummyBot" )
    ircConnect ( theBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function event_ircOnConnect ( theBot )
    setTimer ( ircJoinChannel, 2000, 1, theBot, "#testchannel" )
end

function event_ircOnText ( theBot, channel, sender, message )
    if message:find( "!istopiclocked" ) then
        local channelMode = ircGetChannelMode( theBot, channel )
        if channelMode:find( "t" ) then -- t = TOPIC_LOCK
            ircSendMessage ( theBot, channel, "Yes, the topic is locked." )
        else
            ircSendMessage ( theBot, channel, "Nope, it's not locked... SO CHANGE IT NOW!" )
        end
    end
end
```

See Also
--------
