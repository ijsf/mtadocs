This function will ban the specified [serial](/serial.md "wikilink") number from the server.

Syntax
------

``` lua
bool banSerial ( string theSerial )         
```

### Required Arguments

-   **theSerial:** The serial to ban from this server

### Returns

Returns *true* if the serial was banned succesfully, *false* if invalid arguments are specified.

Example
-------

This example lets a client (console or player) ban a serial if he has ACL rights.

``` lua
--Add the "banserial" command handler
function banSerialCommand ( theClient, commandName, bannedSerial )

    -- Give the player a nice error if he doesn't have rights
    if ( hasObjectPermissionTo ( theClient, "function.banSerial" ) ) 

        --Ban the serial
        banSerial ( bannedSerial )
        outputChatBox ( "banserial: Serial " .. bannedSerial .. " successfully banned", theClient )
    else
        outputChatBox ( "banserial: You don't have enough permissions", theClient )
    end

end
addCommandHandler ( "banserial", banSerialCommand )
```

See Also
--------
