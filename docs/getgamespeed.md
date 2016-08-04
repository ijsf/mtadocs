This function gets the current game speed value.

Syntax
------

``` lua
float getGameSpeed ( )
```

### Returns

Returns a *float* representing the speed of the game.

Example
-------

<section name="Server and Client" class="both" show="true">
This example adds a 'gamespeed' console command that prints the game speed to the chatbox.

``` lua
function gameSpeedValue( )
    local speed = getGameSpeed( )
    outputChatBox( "Game speed is currently set to " .. speed .. "." )
end
addCommandHandler( "gamespeed", gameSpeedValue )
```

</section>
See Also
--------

[ru:getGameSpeed](/docs/ru:getgamespeed.md "wikilink")
