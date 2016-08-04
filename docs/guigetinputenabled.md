This function checks whether user input is focused on the GUI or the game.

Syntax
------

``` lua
bool guiGetInputEnabled ( )
```

### Returns

Returns *true* if input is focused on GUI, *false* if it's focused on the game.

Example
-------

This example adds a command with which you can check whether the input is focused on GUI or game.

``` lua
addCommandHandler( "checkinput", function ()
    if guiGetInputEnabled( ) then
        outputChatBox( "Your input focus is currently on GUI." )
    else 
        outputChatBox( "Your input focus is currently on game." )
    end
end )
```

See Also
--------
