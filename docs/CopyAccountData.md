This function copies all of the data from one [account](/docs/account.md "wikilink") to another.

Syntax
------

``` lua
bool copyAccountData ( account theAccount, account fromAccount )
```

### Required Arguments

-   **theAccount:** The account you wish to copy the data *to*.
-   **fromAccount:** The account you wish to copy the data *from*.

### Returns

Returns a *true* if the accounts were valid, *false* otherwise.

Example
-------

This example copies the account data from the 'guest' to a registered account when they login

``` lua
function copyDataOnLogin ( previousAccount, currentAccount, autoLogin)
  copyAccountData ( currentAccount, previousAccount )
end
addEventHandler ( "onPlayerLogin", getRootElement(), copyDataOnLogin )
```

See Also
--------

[ru:copyAccountData](/docs/ru:copyAccountData.md "wikilink") [ar:copyAccountData](/ar:copyAccountData.md "wikilink") [pl:copyAccountData](/pl:copyAccountData.md "wikilink")
