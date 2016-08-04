Returns a list of key names that are bound to the specified game [control](/Control_names.md "wikilink") or console command.

Syntax
------

``` lua
table getBoundKeys ( string command/control )
```

### Required Arguments

-   **command/control:** the name of a game control or a console command. See the [control names](/control_names.md "wikilink") page for valid controls.

### Returns

If one or more keys are bound to the specified control or console command, a table is returned indexed by the names of the keys and containing key states as values. If no keys are bound or an invalid name was passed, returns *false*.

Example
-------

This code adds a command handler with which you can check out the keybinds for any game control. As an example, typing "/keys forwards" would list all the keys which you can press to make the player walk forward.

``` lua
function keysCommand ( command, controlName )
    if not controlName then                     -- make sure they specified a control name
        outputChatBox ( "No control name specified", 255, 0, 0 )
        return
    end
    local keys = getBoundKeys ( controlName )   -- get the keys bound to this control
    if not keys then                            -- make sure the control name is valid and any keys are bound to it
        outputChatBox ( "No keys bound to " .. controlName, 255, 0, 0 )
        return
    end
    outputChatBox ( "Keys bound to " .. controlName .. ":", 0, 255, 0 )
    for keyName, state in pairs(keys) do
        outputChatBox ( keyName, 0, 255, 0 )
    end
end

addCommandHandler ( "keys", keysCommand )
```

See Also
--------
