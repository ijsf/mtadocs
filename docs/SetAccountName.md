This function is used to change existing [accounts](/docs/account.md "wikilink") name.

Syntax
------

``` lua
bool setAccountName ( element player, string oldAccount, string newAccount )
```

### Required Arguments

-   **player**: The player who called the function.
-   **oldAccount**: The account you want to change.
-   **newAccount**: The name you wanna to apply old account on it.

### Returns

Returns *true* if account was successfully changed, *false* if the old account does not exist/ the new account exist.

Code
----

<section name="Function source" class="server" show="true">
``` lua
setAccountName = function ( plr, old, new )
    if old and new then
        local oldAccount, newAccount, newPass = getAccount ( old ), getAccount ( new ), "mta"..math.random(10000,100000)
        if oldAccount and not newAccount then
            if addAccount ( new, newPass ) then
                local newAccount = getAccount ( new )
                local player = getAccountPlayer ( oldAccount )
                for index, value in pairs ( getAllAccountData ( oldAccount ) ) do
                    setAccountData ( newAccount, index, value )
                end
                for index, value in ipairs ( aclGroupList ( ) ) do
                    if isObjectInACLGroup ( "user."..old, value ) then
                        aclGroupAddObject ( value, "user."..new )
                        aclGroupRemoveObject ( value, "user."..old )
                    end
                end
                if player then
                    logOut ( player )
                    logIn ( player, newAccount, newPass )               
                    if plr == player then
                        outputChatBox ( "* Your new account and password: [ "..new.." ] [ "..newPass.." ].", player, 255, 255, 0, true )
                    else
                        outputChatBox ( "* Your new account and password: [ "..new.." ] [ "..newPass.." ].", player, 255, 255, 0, true )
                        outputChatBox ( "* New account and password: [ "..new.." ] [ "..newPass.." ].", plr, 255, 255, 0, true )
                    end
                else
                    outputChatBox ( "* New account and password: [ "..new.." ] [ "..newPass.." ].", plr, 255, 255, 0, true )
                end
                setTimer ( removeAccount, 100, 1, oldAccount )
                return true
            end
        end
    end
    return false
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example will change account name.

``` lua
addCommandHandler ( "chgAccName", function ( player, _, old, new )
    setAccountName ( player, old, new )
end )
```

</section>
Author
------

Created By 3NAD.

See Also
--------
