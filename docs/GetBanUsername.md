This function will return the username of the specified [ban](/ban.md "wikilink").

Syntax
------

``` lua
string getBanUsername ( ban theBan )
```

### Required Arguments

-   **theBan:** The [ban](/ban.md "wikilink") in which you wish to retrieve the username of.

### Returns

Returns a *string* of the username if everything was successful, *false* if invalid arguments are specified if there was no username specified for the [ban](/ban.md "wikilink").

Example
-------

``` lua
function retrieveBan(theBan)
    local ban = getBanUsername(theBan)
    if ban then
        outputChatBox("The following bans username is: "..ban, getRootElement(), 255,255,255, true)
    end
end
```

See Also
--------

[ru:getBanUsername](/ru:getBanUsername.md "wikilink")
