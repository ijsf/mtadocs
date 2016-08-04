This function retrieves the server's name.

Syntax
------

``` lua
string getServerName ( )
```

### Returns

A string containing the server's name.

Example
-------

This example creates a console command that outputs the server's name to the chatbox.

``` lua
function outputServerName ( )
    outputChatBox ( getServerName( ) )
end

-- Add console command 'getServerName'
addCommandHandler ( "getServerName", outputServerName )
```

See Also
--------
