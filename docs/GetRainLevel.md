This function is used to get the current rain level.

**Note:** The server can only return the rain level if it has actually been set by script, otherwise it will return *false*.

Syntax
------

``` lua
float getRainLevel( )
```

### Returns

Returns the rain level as a number.

Example
-------

<section name="Client" class="client" show="true">
**Example:** Sets the rain (So it can detect it) before returning it. (In this case, when resource starts.)

``` lua
addEventHandler("onClientResourceStart", getResourceRootElement(), function()
    setRainLevel(math.random(5))
end)
function returnRain()
    local rain = getRainlevel()
    if(rain >= 1) then
        outputChatBox("Looks like it's going to be a rainy day!",255,130,130,false)
    else
        outputChatBox("Surprisingly dry!",255,130,130,false)
    end
end
addCommandHandler("rain", returnRain)
```

</section>
<section name="Server" class="server" show="true">
**Example:** Sets the rain (So it can detect it) before returning it. (In this case, when resource starts.)

``` lua
addEventHandler("onResourceStart", getResourceRootElement(), function()
    setRainLevel(math.random(5))
end)

function returnRain(player)
    local rain = getRainlevel()
    if(rain >= 1) then
        outputChatBox("Looks like it's going to be a rainy day!",player,255,130,130,false)
    else
        outputChatBox("Surprisingly dry!",player,255,130,130,false)
    end
end
addCommandHandler("rain", returnRain)
```

</section>
See Also
--------
