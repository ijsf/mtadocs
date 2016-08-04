This function will add a [ban](/docs/ban.md "wikilink") for the specified IP/username/serial to the server.

Syntax
------

``` lua
ban addBan ( [ string IP, string Username, string Serial, player responsibleElement, string reason, int seconds = 0 ] )         
```

**Note:** One of the three: IP, Username or Serial have to be specified.

### Required Arguments

-   **IP:** The IP to be banned. If you don't want to ban by IP, set this to *nil*.

**or**

-   **Username:** The [MTA Community](http://community.mtasa.com/) username to be banned (now obsolete). If you don't want to ban by username, set this to *nil*.

**or**

-   **Serial:** The serial to be banned. If you don't want to ban by serial, set this to *nil*.

*' or any combination.*'

### Optional Arguments

-   **responsibleElement:** The element that is responsible for banning the IP/username/serial. This can be a player or the root ([getRootElement](/docs/getRootElement.md "wikilink")()).
-   **reason:** The reason the IP/username/serial will be banned from the server.
-   **seconds:** The amount of seconds the player will be banned from the server for. This can be 0 for an infinite amount of time.

### Returns

Returns the new [ban](/docs/ban.md "wikilink") if the IP/username/serial was banned successfully, *false* if invalid arguments are specified.

Example
-------

This example bans a player's IP with the reason “Requested” when they type "/ban-me".

``` lua
function banMe ( source, command ) -- The function header and where source is defined
    local ipToBan = getPlayerIP ( source ) -- Get the player's IP
    addBan ( ipToBan, nil, nil, source, "Requested" ) -- Ban him with the reason; Requested
end
addCommandHandler ( "ban-me", banMe ) -- Make it trigger when a player types "/ban-me"
```

Example 2
---------

This example add command to ban player serial.

``` lua
function banSerial( source, command, noob, reason )
   if ( noob ) then
      local theNoob = getPlayerFromName( noob )
      if ( theNoob ) then
         local theNoobSerial = getPlayerSerial( theNoob )
         addBan( nil, nil, theNoobSerial, source, reason )
      end
   end
end
addCommandHandler( "ban-serial", banSerial )
```

See Also
--------

[ru:addBan](/docs/ru:addBan.md "wikilink")
