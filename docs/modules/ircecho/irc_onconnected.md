This is called when the IRC Module has successfully connected to a server

Syntax
------

``` lua
function irc_onConnected (  )
```

Example
-------

**Example 1:** This script outputs that the server has connected to IRC

``` lua
function irc_onConnected( )
    outputServerLog( "IRC Connected!" )
end
```

See also
--------
