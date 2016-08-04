This function returns a string which tell you which MTA version player uses. From DP2.1 onwards.

Syntax
------

``` lua
string getMTAVersion( )
```

### Required Arguments

None

### Returns

A *string* - currently: “1.0 dp2.1”

Example
-------

``` lua
function checkVersion( )
    if getMTAVersion( ) ~= "1.0 dp2.1" then
        outputChatBox( "Download the latest MTA:SA DM and come back!" )
    end
end
addEventHandler( "onClientResourceStart", getResourceRootElement(), checkVersion )
```

See Also
--------
