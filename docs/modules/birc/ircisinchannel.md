This function can be used to check whether ircbot or a specified user is in a channel.

Syntax
------

``` lua
bool ircIsInChannel ( ircbot theBot, string channel, [ string user ] )
```

### Required Arguments

-   **theBot:** The ircbot which presence in the channel is checked or is in the channel.
-   **channel:** The channel which should be checked.

### Optional Arguments

-   **user:** The name of the user whose presence in the channel you want to check. If not specified, checks if the ircbot is in the channel.

### Returns

Returns *true* if the ircbot or specified user is in the channel, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* makes it connect to a server and join a channel. It also includes an IRC command '!finduser' which can be used to check if a specified user in in the channel.

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
    if message:find( "!finduser" ) then
        local user = message:sub( 11 ) -- subtract "!finduser " from the message
        if ircIsInChannel( theBot, channel, user ) then 
            ircSendMessage( theBot, channel, "Yes, " .. user .. " is here!" )
        else
            ircSendMessage( theBot, channel, "Nope, " .. user .. " isn't here!" )
        end
    end
end
```

See Also
--------
