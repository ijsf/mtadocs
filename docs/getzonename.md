This function allows you to retrieve the zone name of a certain location.

*Note that between versions 1.1 and 1.3.0-3749 the default value for **citiesonly** was incorrect when called the client side. The work around for clients before 1.3.0-3749 is to always declare a value for **citiesonly**. Server side getZoneName was unaffected.*

Syntax
------

``` lua
string getZoneName ( float x, float y, float z, [bool citiesonly=false] )
```

### Required Arguments

-   **x:** The X axis position
-   **y:** The Y axis position
-   **z:** The Z axis position

### Optional Arguments

-   **citiesonly**: An optional argument to choose if you want to return the city name (eg Las Venturas)

### Returns

Returns the string of the zone name

Example
-------

<section name="Server" class="server" show="true">
**Example 1:** This example shows you how to return a zone name by doing /loc x y z in the chatbox or just loc x y z in console ( replace x, y and z with the co-ords you wanna check, eg /loc 1200 523 12.3 )

``` lua
function playerLoc ( source, command, x, y, z )
  local location = getZoneName ( x, y, z )
  outputChatBox ( "* Location: " .. location, getRootElement(), 0, 255, 255 ) -- Output the zone name
end
addCommandHandler( "loc", playerLoc )
```

**Example 2:** This example will tell you what zone a specified player is in when the “getloc” console command is used.

``` lua
function scriptGetLoc ( source, command, playername ) --when getloc is called
  local thePlayer = getPlayerFromName ( playername ) --get the player from nickname
  if ( thePlayer ~= false ) then --if there is a player from the nickname
    local x, y, z = getElementPosition ( player )
    local location = getZoneName ( x, y, z )
    local city = getZoneName ( x, y, z, true )
    outputChatBox ( playername .. " is at " .. location .. " (" .. city .. ")", source ) --announce his zone
  else outputChatBox ( "Player does not exist" )
  end
end
addCommandHandler( "getloc", scriptGetLoc ) -- add a command "getloc" which initiates "scriptGetloc" function
```

</section>
See Also
--------

[ru:getZoneName](/docs/ru-getzonename.md "wikilink")
