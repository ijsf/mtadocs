Syntax
------

``` lua
bool isChatVisible ( )
```

### Returns

Returns *true* if the chat is visible, *false* otherwise.

Example
-------

This example does the same thing as *showchat* command does.

``` lua
addCommandHandler("sc",
    function ()
        showChat(not isChatVisible())
    end)
```

See Also
--------

[ru:isChatVisible](/docs/ru:ischatvisible.md "wikilink")
