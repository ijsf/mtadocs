This function is used for testing scripts written using [guiCreateFont](/docs/guiCreateFont.md "wikilink"), [dxCreateFont](/dxCreateFont.md "wikilink"), [dxCreateShader](/dxCreateShader.md "wikilink") and [dxCreateRenderTarget](/dxCreateRenderTarget.md "wikilink").

Each one of the 3 test modes should be used in turn to help highlight any potential problems.

Syntax
------

``` lua
bool dxSetTestMode ( string testMode )
```

### Required Arguments

-   **testMode :** The test mode to be set. It can be one of the following values:
    -   **none :** Test mode disabled
    -   **no\_mem:** Simulate no free video memory available for MTA.
    -   **low\_mem:** Simulate little free video memory available for MTA.
    -   **no\_shader:** Simulate shaders failing validation.

### Returns

Returns *true* if the test mode was successfully set, *false* otherwise.

Example
-------

With this example you can use /setmode command to set the test mode.

``` lua
local testValues = {
    ["none"] = true,
    ["no_mem"] = true,
    ["low_mem"] = true,
    ["no_shader"] = true
}

function testmode( cmd, value )
    if testValues[value] then
        dxSetTestMode( value )
        outputChatBox( "Test mode set to " .. value .. ".", 220, 175, 20, false )
    else
        outputChatBox( "Invalid test mode entered.", 245, 20, 20, false )
    end
end
addCommandHandler( "setmode", testmode )
```

See Also
--------
