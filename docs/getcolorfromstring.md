This function will extract Red, Green, Blue and Alpha values from a hex string you provide it. These strings follow the same format as used in HTML, with addition of the Alpha values.

Syntax
------

``` lua
int int int int getColorFromString ( string theColor )
```

### Required Arguments

-   **theColor:** A string containing a valid color code.

  
Valid strings are:

-   **\#RRGGBB**: Colors specified, Alpha assumed to be 255.
-   **\#RRGGBBAA**: All values specified.
-   **\#RGB**: Shortened form, will be expanded internally to RRGGBB, as such it provides a smaller number of colors.
-   **\#RGBA**: As above, shortened - each character is duplicated.

<!-- -->

  
For example:

-   **\#FF00FF** is Red: 255, Green: 0, Blue: 255, Alpha: 255
-   **\#F0F** is Red: 255, Green: 0, Blue: 255, Alpha: 255 (the same as the example above)
-   **\#34455699** is Red: 52, Green: 69, Blue: 86, Alpha: 153

All colors used must begin with a \# sign.

### Returns

Returns four integers in RGBA format, with a maximum value of 255 for each. Each stands for *red*, *green*, *blue*, and *alpha*. Alpha decides transparancy where 255 is opaque and 0 is transparent. *false* is returned if the string passed is invalid (for example, is missing the preceeding \# sign).

Example
-------

<section class="server" name="Server" show="true">
This example will set the blip attached to a player to a color they specify by typing *set\_my\_color \[color\]* in the console.

``` lua
function setPlayerBlipColor ( playerSource, commandName, colorString )
    local red, green, blue, alpha = getColorFromString ( colorString )  -- convert the color string to numbers
    local playerBlip = getBlipAttachedTo ( playerSource )               -- find the blip attached to the player
    if ( playerBlip and red ) then                                      -- check a blip is attached to the player and that a valid color was specified
        setBlipColor ( playerBlip, red, green, blue, alpha )            -- set the player's blip color
    end
end
addCommandHandler ( "set_my_color", setPlayerBlipColor )

-- specify the getBlipAttachedTo function
function getBlipAttachedTo( thePlayer )
    local blips = getElementsByType( "blip" )
    for k, theBlip in ipairs( blips ) do
        if getElementAttachedTo( theBlip ) == thePlayer then
            return theBlip
        end
    end
    return false
end
```

</section>
See Also
--------
