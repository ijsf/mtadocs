This function gets an **online** player from their [serial](/serial.md "wikilink").

Syntax
------

``` lua
player getPlayerFromSerial ( string serial )
```

### Required Arguments

-   **serial**: A string determining the serial of player you want to get.

### Returns

Returns a [player](/player.md "wikilink") element if the specified [serial](/serial.md "wikilink") is owned by an existent player on the server, *false* otherwise.

Code
----

<section name="Server" class="server" show="true">
``` lua
function getPlayerFromSerial ( serial )
    assert ( type ( serial ) == "string" and #serial == 32, "getPlayerFromSerial - invalid serial" )
    for index, player in ipairs ( getElementsByType ( "player" ) ) do
        if ( getPlayerSerial ( player ) == serial ) then
            return player
        end
    end
    return false
end
```

</section>
Example
-------

This example gets a player name from random serial and outputs it in chatbox.

``` lua
outputChatBox( getPlayerName ( getPlayerFromSerial( "AE9EP68QXKHW55LQIAL9C77Q9VJHA00M" ) ) )
```

Author: Tete

Hint: This function can be useful for building up a serial-based system.

See Also
--------
