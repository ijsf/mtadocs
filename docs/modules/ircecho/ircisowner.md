Can be used to check if the user has founderrights in an channel

Syntax
------

``` lua
function ircIsOwner ( IRCConnection irc, string channel, string nick )
```

### Required arguments

-   **irc:** The IRCConnection
-   **channel:** The channel that you want to check on
-   **nick:** The person that you want to check on

Example
-------

**Example 1:** This script can be used from irc, so that people with founderrights or higher can use !unban

``` lua
function irc_onPrivMsg( szChannel, szNick, szText )
    if string.find( szText, "!unban" ) == 1 then
        if ( ircIsOwner( pIRC, szChannel, szNick ) ) then
            unbanIP(string.sub(szText, 7))
        end
    end
end
```
