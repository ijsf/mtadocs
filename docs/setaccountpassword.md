This function sets the password of the specified [account](/docs/account.md "wikilink").

Syntax
------

``` lua
bool setAccountPassword ( account theAccount, string password[, string passwordType="plaintext"] )
```

### Required Arguments

-   **theAccount:** the account whose password you want to set
-   **password:** the password

### Optional Arguments

### Returns

Returns *true* if the password was set correctly, *false* otherwise.

### Limits

Unless hashed with sha256 (length 97) or md5 (length 32), the following limits apply:

-   Minimal account password length is 1 character.
-   Maximum account password length is 30 characters.
-   Account password can not be equal to "\*\*\*\*\*"

Example
-------

This example allows a user to change their password with a command.

``` lua
function ChangePlayerPassword(player, command, oldpass, newpass)
    -- get the account the player is currently logged into
    local account = getPlayerAccount(player)
    if (account) then
        -- if its only a guest account, do not allow the password to be changed
        if (isGuestAccount(account)) then
            outputChatBox("You must be logged into an account to change your password.", player) 
            -- end the function
            return
        end
        
        -- check that the old password is correct
        local password_check = getAccount(getAccountName(account), oldpass)
        if (password_check) then
            -- check the length of the new password
            if (string.len(newpass)>=5) then
                setAccountPassword(account,newpass)
            else
                outputChatBox("Your new password must be at least 5 characters long.", player)
            end
        else
            outputChatBox("Old password invalid.", player)
        end
    end
end
addCommandHandler("changepass", ChangePlayerPassword)
```

See Also
--------

[ar:setAccountPassword](/docs/ar:setaccountpassword.md "wikilink") [es:setAccountPassword](/es:setAccountPassword.md "wikilink")
