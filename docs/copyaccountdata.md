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

[ru:copyAccountData](/docs/ru-copyaccountdata.md "wikilink") [ar:copyAccountData](/docs/ar-copyaccountdata.md "wikilink") [pl:copyAccountData](/docs/pl-copyaccountdata.md "wikilink")
