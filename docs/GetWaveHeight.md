This function returns the current wave height.

Syntax
------

``` lua
float getWaveHeight()
```

### Returns

Returns the height as a [float](/float.md "wikilink"), *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example changes the wave height to the given amount.

``` lua
function scriptWave ( thePlayer, command, height )
    local oldHeight = getWaveHeight()
    height = tonumber ( height )
    success = setWaveHeight ( height )
    if ( success ) then
        outputChatBox ( "The old wave height was: " .. oldHeight .. "; " .. getPlayerName ( thePlayer ) .. " set it to: " .. height )
    else
        outputChatBox ( "Invalid number." )
    end
end
addCommandHandler ( "setwave", scriptWave )
```

</section>
See Also
--------
