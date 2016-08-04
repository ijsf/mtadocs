This function allows you to retrieve the zone name of an element (eg. Verdant Bluffs or Ocean Docks)

The same can be achieved client side by getting element coordinates and using [GetZoneName](/docs/getzonename.md "wikilink").

Syntax
------

``` lua
string getElementZoneName ( element theElement, [bool citiesonly=false] )
```

### Required Arguments

-   **theElement:** The element which you'd like to retrieve the zone name from

### Optional Arguments

-   **citiesonly**: An optional argument to choose if you want to return the city name (eg Las Venturas)

### Returns

Returns the string of the elements zone name.

Example
-------

This example shows you how to return your own location by doing /loc in the chatbox or just loc in console

``` lua
function playerloc ( source )
    local playername = getPlayerName ( source )
    local location = getElementZoneName ( source )
    outputChatBox ( "* " .. playername .. "'s Location: " .. location, getRootElement(), 0, 255, 255 ) -- Output the player's name and zone name
end
addCommandHandler ( "loc", playerloc )
```

See Also
--------
