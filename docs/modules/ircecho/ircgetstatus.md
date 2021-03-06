Can be used to get the given nick's access level on a channel.

**Returns the following numbers:**

-   0: Normal user
-   1: Voice (+v - +nick)
-   2: Half-Op (+h - %nick)
-   3: Operator (+o - @nick)
-   4: Admin/Super-Op (+a - &nick)
-   5: Owner (+q - ~nick)

Syntax
------

``` lua
function ircGetStatus ( IRCConnection irc, string channel, string nick )
```

### Required arguments

-   **irc:** The IRCConnection
-   **channel:** The channel that you want to check on
-   **nick:** The person that you want to check on

Example
-------

**Example 1:** This script can be used from irc, so people can check their rights

``` lua
function irc_onPrivMsg( szChannel, szNick, szText )
    if string.find( szText, "!rights" ) == 1 then
        ircMessage( pIRC, szChannel,  szNick .. ", you have level " .. tostring( ircGetStatus( pIRC, szChannel, szNick ) )
    end
end
```
