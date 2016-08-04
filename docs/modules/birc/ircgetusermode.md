This function returns the user mode of user in specified channel. The specified has to be in that channel.

Syntax
------

``` lua
string ircGetUserMode ( ircbot theBot, string channel, string user )
```

### Required Arguments

-   **theBot:** The ircbot which is in the channel
-   **channel:** The name of the channel which channel mode you want to get
-   **user:** The name of the user whose user mode you want to return

### Returns

Returns a [string](/docs/string.md "wikilink") containing a series of symbols, each representing a user mode. Symbols are

-   **+:** user is voiced in the channel
-   **%:** user is a channel half-operator
-   **@:** user is a channel operator
-   **&:** user is a channel super-operator
-   **~:** user is the channel owner

If user does not have any modes on that channel, returns an empty string or *false* if invalid arguments were passed.

Example
-------

This example creates a function which can be used to check whether a user is voiced in a channel.

``` lua
function isUserVoiced( theBot, channel, user )
    local botName = ircGetName( theBot )
    if botName then -- if the bot given was valid (it has a name)
        if ircIsInChannel( theBot, channel, user ) then -- if the user is in channel
            local userMode = ircGetUserMode( theBot, channel, user )
            if userMode and userMode:find( "+" ) then -- if valid arguments were passed, and '+' symbol is found in the user mode
                return true
            end
        end
    end
    return false
end
```

See Also
--------
