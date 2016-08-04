This function returns whether the ingame console window is visible or not.

Syntax
------

``` lua
bool isConsoleActive ()
```

### Returns

Returns *true* if the console is visible, *false* if not.

Example
-------

This example does...

``` lua
function consoleactiveCommand(arg)
    local active = "not active."
    if (isConsoleActive()) then active = "active." end
    outputChatBox("Your console is " .. active)
end
addCommandHandler("consoleactive", consoleactiveCommand)
```

See Also
--------
