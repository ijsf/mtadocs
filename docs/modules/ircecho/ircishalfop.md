Can be used to check if the user has Halfop or higher

Syntax
------

``` lua
function ircIsHalfop ( IRCConnection irc, string channel, string nick )
```

### Required arguments

-   **irc:** The IRCConnection
-   **channel:** The channel that you want to check on
-   **nick:** The person that you want to check on

Example
-------

**Example 1:** This script can be used from irc, so that people with Halfop or higher can use !asay

``` lua
function irc_onPrivMsg( szChannel, szNick, szText )
    if string.find( szText, "!asay" ) == 1 then
        if ( ircIsHalfop( pIRC, szChannel, szNick ) ) then
            local Message = string.sub(szText, 6)
            outputChatBox("The admin says: " .. Message, getRootResource(), 255, 0, 0)
        end
    end
end
```

See also
--------
