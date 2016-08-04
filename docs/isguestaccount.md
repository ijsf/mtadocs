This function checks to see if an [account](/docs/account.md "wikilink") is a guest account. A guest account is an account automatically created for a user when they join the server and deleted when they quit or login to another account. Data stored in a guest account is not stored after the player has left the server. As a consequence, this function will check if a player is logged in or not.

Syntax
------

``` lua
bool isGuestAccount ( account theAccount )
```

### Required Arguments

-   **theAccount:** The account you want to check to see if it is a guest account.

### Returns

Returns *true* if the account is a guest account, *false* otherwise.

Example
-------

This example shows how you could create a *call\_admin* function that only could be run by registered users.

``` lua
function callAdmin ( playerSource )
    -- get the account of the user trying to use this function first
    sourceAccount = getPlayerAccount ( playerSource )
    -- if they're a guest
    if isGuestAccount ( sourceAccount ) then
        -- tell them to register
        outputConsole ( "Please register to use this function!", playerSource )
    else
        -- your code to call the admin would go here
    end
end
-- attach the function 'callAdmin' as a handler to the command "call_admin"
addCommandHandler ( "call_admin", callAdmin )
```

See Also
--------

[ar:isGuestAccount](/docs/ar:isguestaccount.md "wikilink")
