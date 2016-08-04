This functions logs the given player in to the given [account](/account.md "wikilink"). You need to provide the password needed to log into that account.

Syntax
------

``` lua
bool logIn ( player thePlayer, account theAccount, string thePassword )
```

### Required Arguments

-   **thePlayer:** The player to log into an account
-   **theAccount:** The account to log the player into
-   **thePassword:** The password needed to sign into this account

### Returns

Returns *true* if the player was successfully logged into the given account. Returns *false* or *nil* if the log in failed for some reason, ie. the player was already logged in to some account (use [logOut](/logOut.md "wikilink") first), if the account was already in use or if it failed for some other reason.

Example
-------

``` lua
function loginPlayer ( thePlayer, command, username, password )
    local account = getAccount ( username, password ) -- Return the account
        if ( account ~= false ) then -- If the account exists.
            logIn ( thePlayer, account, password ) -- Log them in.
        else
            outputChatBox ( "Wrong username or password!", thePlayer, 255, 255, 0 ) -- Output they got the details wrong.
        end
end
addCommandHandler ( "log-in", loginPlayer ) -- Make it trigger for "/log-in", NOTE: /login is hardcored and cannot be used.
```

See Also
--------

[ru:logIn](/ru:logIn.md "wikilink") [ar:logIn](/ar:logIn.md "wikilink")
