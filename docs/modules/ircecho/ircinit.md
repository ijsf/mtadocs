Initializes the module for use in the script. Must be ran in the scripts you want to use with the echo

Syntax
------

``` lua
function ircInit()
```

Example
-------

**Example 1:** This example initializes the module on resource startup

``` lua
function onResourceStart( res )
    if ( res == getThisResource () ) then
        ircInit()
        outputServerLog( "Initialized IRC for " .. getResourceName( res ) )
    end
end

addEventHandler( "onResourceStart", getRootElement(), onResourceStart )
```

See also
--------
