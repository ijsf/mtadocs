Syntax
------

``` lua
bool isBrowserDomainBlocked ( string address [, bool isURL = false] )
```

### Required arguments

-   **address:** A website URL

### Optional arguments

-   **isURL:** *true* if *address* should be parsed as URL, *false* otherwise.

### Returns

Returns *false* if the URL is able to be loaded, *true* if it is blocked and *nil* if an invalid domain/URL was passed.

Example
-------

``` lua
--Check the state of wiki.mtasa.com
if ( isBrowserDomainBlocked ( "wiki.mtasa.com" ) ) then
    --If it is blocked.
    outputChatBox("wiki.mtasa.com is blocked and can't be loaded right now!")
else
    --If it is not blocked. (Was accepted by the user)
    outputChatBox("wiki.mtasa.com is not blocked and ready to be loaded!")
end
```

See Also
--------
