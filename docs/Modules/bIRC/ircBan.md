This function can be used to ban-kick user from the specified channel. The specified often needs to have suitable privileges in order for this to work.

Syntax
------

``` lua
bool ircBan ( ircbot theBot, string channel, string user, [ int formatType = 2, string reason = "" ] )
```

### Required Arguments

-   **theBot:** The ircbot which is going to do the banning
-   **channel:** The channel where user should be banned from
-   **user:** The user who should be banned

### Optional Arguments

-   **formatType:** The ban mask type which should be used for banning. A list can be found in function
-   **reason:** The reason for the ban

### Returns

Returns *true* if passed arguments were valid, *false* otherwise.
**Note:** Does not return *true* if the user was successfully banned or *false* if it failed. You can check if the user was kicked by using callback and if the a channel mode was set by using callback .

Example
-------

This example creates an ircbot called *DummyBot*, makes it connect to a server and join a channel. It also includes an IRC command '!ban' which can be used to ban users from the channel.

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
            ircBan ( theBot, channel, params[2] )
        end
    end
end
```

See Also
--------
