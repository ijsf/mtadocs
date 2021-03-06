This function can be used to kick user from the specified channel. The specified often needs to have suitable privileges in order for this to work.

Syntax
------

``` lua
bool ircKick ( ircbot theBot, string channel, string user, [ string reason = "" ] )
```

### Required Arguments

-   **theBot:** The ircbot which is going to do the kicking
-   **channel:** The channel where user should be kicked from
-   **user:** The user who should be kicked

### Optional Arguments

-   **reason:** The reason for the kick

### Returns

Returns *true* if passed arguments were valid, *false* otherwise.
**Note:** Does not return *true* if the user was successfully kicked or *false* if it failed. You can check if the user was kicked by using callback .

Example
-------

This example creates an ircbot called *DummyBot*, makes it connect to a server and join a channel. It also includes an IRC command '!kick' which can be used to kick users from the channel.

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
    if message:find( "!kick" ) then
        local params = split ( message, string.byte (' ') )
        -- params[1] has the string "!kick" which we don't need
        -- params[2] has the user name
        if ircIsInChannel ( theBot, channel, params[2] ) then
            ircKick ( theBot, channel, params[2] )
        end
    end
end
```

See Also
--------
