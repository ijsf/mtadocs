This is called when the IRC Module is attempting to connect to a server

Syntax
------

``` lua
function irc_onConnecting ( string IP, int Port )
```

### Required arguments

-   **IP:** The IP/Hostname of the server you are trying to connect to
-   **Port:** The Port of the IRC Server you are trying to connect to

Example
-------

**Example 1:** This script outputs to the server console that it is attempting a connection

``` lua
function irc_onConnecting( IP, Port )
    outputServerLog( "Connecting to IRC (" .. IP .. ":" .. tostring( Port ) .. ")" )
end
```

See also
--------
