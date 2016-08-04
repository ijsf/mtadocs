This event is triggered when the local player enters text in the console. Note that, if you want to add custom console commands, it is easier to use the [addCommandHandler](/docs/addCommandHandler.md "wikilink") function.

Parameters
----------

``` lua
string text
```

-   **text:** the text line that was entered.

Example
-------

This example outputs any text you input into the console.

``` lua
function consoleCheck(text)
    outputChatBox("You entered into the console: "..text,255,255,0)
end
addEventHandler("onClientConsole",getLocalPlayer(),consoleCheck)
```

See Also
--------

### Other client events

### Client event functions
