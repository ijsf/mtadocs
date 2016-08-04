Can be used to check if the user has superops (aka Protection) or higher

Syntax
------

``` lua
function ircIsSuper ( IRCConnection irc, string channel, string nick )
```

### Required arguments

-   **irc:** The IRCConnection
-   **channel:** The channel that you want to check on
-   **nick:** The person that you want to check on

Example
-------

**Example 1:** This script can be used from irc, so that people with superops or higher can use !ban

``` lua
function irc_onPrivMsg( szChannel, szNick, szText )
    if string.find( szText, "!ban" ) == 1 then
        if ( ircIsSuper( pIRC, szChannel, szNick ) ) then
            local thePlayer = getPlayerFromNick(string.sub(szText, 5))
            if (thePlayer) then
                banPlayer( thePlayer )
            end
        end
    end
end
```
