<lowercasetitle/>

This serverside useful function returns an account from its name, if it does exist.

Syntax
------

``` lua
account getAccountFromName ( string accountname )
```

### Required Arguments

-   **accountName**: The name of the account you want to retrieve.

Code
----

<section name="Server" class="server" show="true">
``` lua
function getAccountFromName ( name )
    return getAccount ( name ) or false
end
```

</section>
Author: SunArrow

Example
-------

This example tells any player who uses */checkaccountname* command if their nickname is used by an account or not.

``` lua
function outputUsernameAvailability(player)
    local nick = getPlayerName(player)
    if getAccountFromName(nick) then
        outputChatBox("Your nickname is already used by an account.",player,255,0,0)
   else
      outputChatBox("Your nickname is free to use by a new account.",player,0,255,0)
   end
end
addCommandHandler("checkaccountname",outputUsernameAvailability)
```

See Also
--------
