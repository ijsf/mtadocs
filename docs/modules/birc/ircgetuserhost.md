This function returns the hostmask of a specified user in format user@host. The specified has to be in one of the channels the specified user is in.

Syntax
------

``` lua
string ircGetUserHost ( ircbot theBot, string user )
```

### Required Arguments

-   **theBot:** The ircbot which is in the channel
-   **user:** The user whose hostmask you want to get

### Returns

Returns the host of specified user if it could be retrieved, or *false* if it failed or invalid arguments were passed.

Example
-------

This example creates an ircbot called *DummyBot* makes it connect to a server and join a channel. It also includes an IRC command '!ban' which can be used to ban users (unable to talk or join) from IRC without kicking them from the channel.

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
    if message:find( "!ban" ) then
        local params = split ( message, string.byte (' ') )
        -- params[1] has the string "!ban" which we don't need
        -- params[2] has the user name
        if ircIsInChannel ( theBot, channel, params[2] ) then
            local userHost = ircGetUserHost ( theBot, params[2] )
            if userHost then -- if user host was successfully received
                local hostMask = ircFormatHost ( params[2] .. "!" .. userHost )
                if hostMask then -- and if formatting was successful
                    ircSetChannelMode ( theBot, channel, "+b " .. hostMask )
                end
            else
                ircSendMessage ( theBot, channel, "Failed to retrieve user host!" )
            end
        end
    end
end
```

See Also
--------
