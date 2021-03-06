This function is used to change the name of the specified .

Syntax
------

``` lua
bool ircSetName ( ircbot theBot, string name )
```

### Required Arguments

-   **theBot:** The ircbot which name you want to change
-   **name:** The new name of the ircbot

### Returns

Returns *true* passed arguments were valid, *false* otherwise.
**Note:** Does not return *true* if ircbot's name was successfully changed or *false* if the bot's name wasn't changed. You can check if the bot had it's name changed by using callback .

Example
-------

This example creates an ircbot called *DummyBot* and makes it connect to a server and join a channel once it has connected. It also includes an IRC command '!setname <name>' which can be used to change ircbot's name.

``` lua
function resourceStart ()
    dummyBot = ircCreateBot ( "DummyBot" )
    ircConnect ( dummyBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function event_ircOnConnect ( theBot )
    setTimer ( ircJoinChannel, 2000, 1, theBot, "#testchannel" )
end

function event_ircOnText ( theBot, channel, sender, message )
    if message:find( "!setname" ) then
        local params = split ( message, string.byte (' ') )
        -- params[1] has the string "!setname" which we don't need
        -- params[2] has the new name
        ircSetName ( theBot, params[2] )
    end
end
```

See Also
--------
