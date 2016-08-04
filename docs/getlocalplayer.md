This function gets the player element of the client running the current script.

Syntax
------

``` lua
player getLocalPlayer ( )
```

### Returns

Returns the local [player](/docs/player.md "wikilink") element.

Example
-------

**Example 1:** This client side function outputs the player's current location to the console.

``` lua
-- we get the local player (we do this outside of the function body so it isn't retrieved every time
-- the function is called, since the local player never changes)

function outputLocalPlayerPosition ( )
    -- get the local player's position
    local px, py, pz = getElementPosition ( getLocalPlayer ( ) )
    -- output it to the console
    outputConsole ( "Your location: " .. px .. " " .. py .. " " .. pz )
end
```

**Example 2:** This client side script makes the local player's camera flash red after being hit.

``` lua
function flashRed ( )
    -- fade out the local player's camera to red during a second
    fadeCamera( false, 1.0, 255, 0, 0 )
    -- set a 500 ms (0.5 sec) timer to fade it back in before it has completely faded out
    setTimer( fadeCamera, 500, 1, true, 1.0 )
end
-- we attach our 'flashRed' function to be a handler of "onClientPlayerDamage" when its source (that is, the hit player) is the local player
addEventHandler( "onClientPlayerDamage", getLocalPlayer ( ), flashRed )
```

See Also
--------

[ru:getLocalPlayer](/docs/ru-getlocalplayer.md "wikilink")
