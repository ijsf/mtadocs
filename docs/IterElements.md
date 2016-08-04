<lowercasetitle/>

This function is useful for **for** loops. You don't have to type *ipairs( getElementsByType( “player” ) )* but simply *iterElements( “player” )*. It's very useful if you have many for loops in your code. [doForAllElements](/docs/doForAllElements.md "wikilink") has to iterate through elements every time you call 1 function per call but this iterates through elements and what you do to/with the elements is up to you.

Syntax
------

``` lua
iterator iterElements( string elementType )
```

### Required Arguments

-   **elementType**: Type of the elements that you want to iterate through.

Code
----

``` lua
function iterElements( elementType )
    local i = 0;
    local tab = getElementsByType( elementType );
    return function( )
        i = i + 1;
        if tab[ i ] then
            return i, tab[ i ];
        end
    end
end
```

Example
-------

This example will iterate through all players and vehicles. It will heal the players, give them $1000, send them a message informing them about the action and fix all vehicles when the resource starts.

``` lua
addEventHandler( "onResourceStart", getResourceRootElement( ),
    function( )
        for _, plr in iterElements( "player" ) do
            setElementHealth( plr, 100 );
            givePlayerMoney( plr, 1000 );
            outputChatBox( "You've just been healed and given $1000!", plr );
        end

        for _, veh in iterElements( "vehicle" ) do
            fixVehicle( veh );
        end
    end
)
```

See Also
--------
