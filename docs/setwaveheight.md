This function sets the wave height to the desired value, the default is 0.

Syntax
------

``` lua
bool setWaveHeight ( float height )
```

### Required Arguments

-   **height:** A float between 0 and 100.

Returns
-------

Returns a boolean value *true* or *false* that tells you if it was successful or not.

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
