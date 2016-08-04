This function will return the time the specified [ban](/docs/ban.md "wikilink") was created, in **seconds**.

Syntax
------

``` lua
int getBanTime ( ban theBan )
```

### Required Arguments

-   **theBan:** The [ban](/docs/ban.md "wikilink") of which you wish to retrieve the time of.

### Returns

-   Returns an integer of the banning time in the format of seconds from the year 1970. Use in conjunction with [getRealTime](/docs/getRealTime.md "wikilink") in order to retrieve detailed information.
-   Returns **false** if invalid arguments were specified or if there was no banning time specified for the [ban](/docs/ban.md "wikilink").

Example
-------

``` lua
function retrieveBan(theBan)
    local ban = getBanTime(theBan)
    if ban then
        outputChatBox("The time of the ban is: " .. ban, root, 255, 255, 255, false)
    end
end
```

See Also
--------

[ru:getBanTime](/docs/ru:getBanTime.md "wikilink")
