This function can be used to change a ban host mask to specified wildcard format.

Syntax
------

``` lua
string ircFormatHost ( string host, [ int formatType = 2 ] )
```

### Required Arguments

-   **host:** The host address that will be reformatted. It needs to be in format “nick!user@host”.

  
**Note:** If you're using this function along with , please remember to add the nick! part yourself to the host as ircGetUserHost only returns the user@host part.

### Optional Arguments

-   **formatType:** The way the host is going to be formatted. Valid values are
    -   0: \*!user@host
    -   1: \*!\*user@host
    -   2: \*!\*@host
    -   3: \*!\*user@\*.host
    -   4: \*!\*@\*.host
    -   5: nick!user@host
    -   6: nick!\*user@host
    -   7: nick!\*@host
    -   8: nick!\*user@\*.host
    -   9: nick!\*@\*.host

  
You can also specify a type of 10 to 19 which correspond to masks 0 to 9, but instead of using only \* wildcard to replace portions of the host, also ? wildcards are used to replace the numbers in the address (host part).

### Returns

Returns a formatted version of the string of the specified host if arguments were valid, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* makes it connect to a server and join a channel. It also includes an IRC command '!formathost <name> <type>' which formats specified users host to specified type if the user is actually in the channel.

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
    if message:find( "!formathost" ) then
        local params = split ( message, string.byte (' ') )
        -- params[1] has the string "!formathost" which we don't need
        -- params[2] has the name of the user
        -- params[3] has the type of the format
        if ircIsInChannel ( theBot, channel, params[2] ) then
            local host = ircGetUserHost ( theBot, params[2] )
            host = ircFormatHost ( params[2] .. "!" .. host, tonumber(params[3]) )
            ircSendMessage ( theBot, channel, params[2] .. "'s formatted host is " .. tostring(host) )
        end
    end
end
```

See Also
--------
