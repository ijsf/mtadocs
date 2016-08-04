This function retrieves whether San Andreas game glitches are enabled or not, set by using [setGlitchEnabled](/docs/setglitchenabled.md "wikilink")

Syntax
------

``` lua
bool isGlitchEnabled ( string glitchName )
```

### Required Arguments

-   **glitchName:** the name of the property to set. Possible values are:

### Returns

Returns *true* if if the glitch was enabled, or *false* if it is disabled.

Example
-------

This example outputs weather the “fastmove” glitch is enabled or not.

``` lua
setGlitchEnabled("fastmove",true) -- Enable the fastmove glitch at resource start.

function checkIsEnabled(thePlayer,command)
    if (isGlitchEnabled("fastmove")) then -- Check weather fastmove is enabled or not.
        outputChatBox("fastmove is enabled.",thePlayer,255,255,0) -- If so, output that it's enabled.
    else
        outputChatBox("fastmove is not enabled.",thePlayer,255,0,0) -- If not, output that it isn't enabled.
    end
end
addCommandHandler("glitch",checkIsEnabled)
```

See Also
--------
