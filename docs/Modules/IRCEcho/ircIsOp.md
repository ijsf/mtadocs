Can be used to check if the user has Op or higher

Syntax
------

``` lua
function ircIsOp ( IRCConnection irc, string channel, string nick )
```

### Required arguments

-   **irc:** The IRCConnection
-   **channel:** The channel that you want to check on
-   **nick:** The person that you want to check on

Example
-------

**Example 1:** This script can be used from irc, so that people with op or higher can use !kick

``` lua
function irc_onPrivMsg( szChannel, szNick, szText )
    if string.find( szText, "!kick" ) == 1 then
        if ( ircIsOp( pIRC, szChannel, szNick ) ) then
            local thePlayer = getPlayerFromNick(string.sub(szText, 6))
            if (thePlayer) then
                kickPlayer( thePlayer )
            end
        end
    end
end
```
