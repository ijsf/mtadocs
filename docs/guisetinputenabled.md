This function enables or disables input focus for the GUI. This means that any keybinds or MTA binds are overidden so that text can be input into an editbox, for example. In other words, keys such as *t* and *y* which activate the chatbox are disabled.

Syntax
------

``` lua
bool guiSetInputEnabled ( bool enabled )
```

### Required Arguments

-   **enabled:** true if input should go to GUI, false if it should go to the game.

### Returns

Returns *true* if input mode could be changed, *false* if invalid parameters are passed.

Example
-------

This example enables or disables the Input.

``` lua
function setInputState()
    guiSetInputEnabled(not guiGetInputEnabled()) -- Disable the Input if Enabled, either Enable it.
    outputChatBox("The input is now ".. (guiGetInputEnabled() and "Enabled" or "Disabled") ..".") -- Output the new Input state.
end
addCommandHandler("input",setInputState) -- Add the command handler attached to the function "setInputState".
```

See Also
--------
