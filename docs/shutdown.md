This function shuts down the server.

Make sure your server ACL setup has function.shutdown object protected.

Syntax
------

``` lua
bool shutdown ( string reason )         
```

### Required Arguments

-   **reason:** the reason why the server has been shut down.

### Returns

Returns *false* if it was not possible to shut down the server.

Example
-------

This command shuts down the server on request

``` lua
addCommandHandler ( "shutdown", function ( player, command, reason )
  if ( hasObjectPermissionTo ( player, "function.shutdown" ) ) then
    shutdown ( reason or "" )
  end
end )
```

See Also
--------
