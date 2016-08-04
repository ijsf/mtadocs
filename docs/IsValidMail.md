<lowercasetitle/>

This function allows you to check if a given string is theoretically a valid e-mail address.

Syntax
------

``` lua
bool isValidMail ( string mail )
```

### Arguments

-   **mail**: A string containing an e-mail address

### Returns

Returns *true* if the e-mail address is valid, *false* if a string was not provided or if it is not an e-mail address.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function isValidMail( mail )
    assert( type( mail ) == "string", "Bad argument @ isValidMail [string expected, got " .. tostring( mail ) .. "]" )
    return mail:match( "[A-Za-z0-9%.%%%+%-]+@[A-Za-z0-9%.%%%+%-]+%.%w%w%w?%w?" ) ~= nil
end
```

</section>
**Author:** SuperHomie

Example
-------

<section name="Server" class="server" show="true">
The next example adds a /registerme command which registers the player who types it, providing that the resource this example is executed in has sufficient ACL permissions.

``` lua
function registerUser( player, commandName, username, password, email )
    if getElementType( player ) == "player" then
        if username and password and email then
            if isGuestAccount( getPlayerAccount( player ) ) then
                if isValidMail( email ) then
                    local newAccount = addAccount( username, password )
                    if newAccount then
                        setAccountData( newAccount, "email", email )
                        logIn( player, newAccount, password )
                        outputChatBox( "Now you're logged in your new account.", player, 0, 255, 0 )
                    else
                        outputChatBox( #password > 30 and "The specified password is too long." or "That account already exists.", player, 255, 0, 0 )
                    end
                else
                    outputChatBox( "The e-mail provided is not valid!", player, 255, 0, 0 )
                end
            else
                outputChatBox( "You are already logged in.", player, 255, 0, 0 )
            end
        else
            outputChatBox( "Syntax: /" .. commandName .. " (username) (password) (email)", player, 255, 255, 255 )
        end
    end
end
addCommandHandler( "registerme", registerUser )
```

</section>
See also
--------
