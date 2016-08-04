This function adds an [account](/docs/account.md "wikilink") to the list of registered accounts of the current server.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **name:** The name of the account you wish to make, this normally is the player's name.
-   **pass:** The password to set for this account for future logins.

### Optional Arguments

-   **allowCaseVariations:** Whether the username is case sensitive (if this is set to true, usernames “Bob” and “bob” will refer to different accounts)

### Returns

Returns an [account](/docs/account.md "wikilink") or *false* if the account already exists or an error occured.

### Limits

-   **name:**
    -   Minimal account name length is 1 character.
    -   Account names are case-sensitive.
    -   Account name can not be equal to "\*\*\*\*\*"
-   **pass:**
    -   Minimal account password length is 1 character.
    -   Maximum account password length is 30 characters.
    -   Account password can not be equal to "\*\*\*\*\*"

Example
-------

**Example 1:** This enables players to register on your server by using /register <password> in the chat window.

``` lua
function registerPlayer ( source, commandName, password )
    -- Check if the password field is blank or not (only blank if they didnt enter one)
    if ( password ~= "" and password ~= nil ) then
        --Attempt to add the account, and save its value in a var
        local accountAdded = addAccount( getPlayerName(source), password )
        if ( accountAdded ) then
            --  Tell the user all is done
            outputChatBox ( "Thank you " .. getPlayerName(source) .. ", you're now registed, you can login with /login", source )
        else
            -- There was an error making the account, tell the user
            outputChatBox ( "Error creating account, contact the server admin", source )
        end
    else
        -- There was an error in the syntax, tell the user the correct syntax.
        outputChatBox ( "Error creating account, correct syntax: /register <password>", source )
    end
end
addCommandHandler ( "register", registerPlayer ) -- add the command handler
```

**This code differs by allowing the user to change their username that they wish to use.**

**Example 2:** This enables players to register on your server by using /register <username> <password> in the chat window.

``` lua
function registerPlayer ( source, commandName, username, password )
        if(password ~= "" and password ~= nil and username ~= "" and username ~= nil) then
                local accountAdded = addAccount(username,password)
                if(accountAdded) then
                        outputChatBox("Thank you " .. getPlayerName(source) .. ", you're now registed, you can login with /login",source)
                else
                        outputChatBox("Error creating account, contact the server admin.",source)
                end
        else
                outputChatBox("Error creating account, correct syntax: /register <nick> <pass>",source)
        end
end
addCommandHandler ( "register", registerPlayer ) -- add the command handler
```

**Example 3:** This code differs again so the user can only register once /register <username> <password>.

``` lua
local bRegisteredOnce = false

function registerPlayer ( source, commandName, username, password )
        if(password ~= "" and password ~= nil and username ~= "" and username ~= nil and bRegisteredOnce == false) then
                local accountAdded = addAccount(username,password)
                if(accountAdded) then
                        outputChatBox("Thank you " .. getPlayerName(source) .. ", you're now registed, you can login with /login",source)
                        bRegisteredOnce = true
                else
                        outputChatBox("Error creating account, contact the server admin.",source)
                end
        else
                if bRegisteredOnce == true then
                    outputChatBox("You already registered on this server!",source)
                else
                    outputChatBox("Error creating account, correct syntax: /register <nick> <pass>",source)
                end
        end
end
addCommandHandler ( "register", registerPlayer ) -- add the command handler
```

See Also
--------

[ar:addAcount](/docs/ar:addacount.md "wikilink") [es:addAcount](/es:addAcount.md "wikilink") [ru:addAccount](/ru:addAccount.md "wikilink") [pl:addAccount](/pl:addAccount.md "wikilink")
