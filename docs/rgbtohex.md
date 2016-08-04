<lowercasetitle></lowercasetitle>

This function retrieves the hex string of a specified color.

Syntax
------

``` lua
string RGBToHex ( int red, int green, int blue [, int alpha = 255] )
```

### Required Arguments

-   **red:** The amount of [red](http://en.wikipedia.org/wiki/RGBA_color_space) in the color (0-255).
-   **green:** The amount of [green](http://en.wikipedia.org/wiki/RGBA_color_space) in the color (0-255).
-   **blue:** The amount of [blue](http://en.wikipedia.org/wiki/RGBA_color_space) in the color (0-255).

### Optional Arguments

-   **alpha:** The amount of [alpha](http://en.wikipedia.org/wiki/RGBA_color_space) in the color (0-255).

### Returns

Returns a string representing the color in hexadecimal.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function RGBToHex(red, green, blue, alpha)
    if((red < 0 or red > 255 or green < 0 or green > 255 or blue < 0 or blue > 255) or (alpha and (alpha < 0 or alpha > 255))) then
        return nil
    end
    if(alpha) then
        return string.format("#%.2X%.2X%.2X%.2X", red,green,blue,alpha)
    else
        return string.format("#%.2X%.2X%.2X", red,green,blue)
    end
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example will output the team color in the chat with HEX format

``` lua
function myTeamColor(Player,Command) -- adding the function
playerTeam = getPlayerTeam(Player)
   if playerTeam then
      r,g,b = getTeamColor(playerTeam)
          if r and g and b then
             outputChatBox("your team color is : "..RGBToHex(r,g,b))
          end
   end
end
addCommandHandler("myteamcolor",myTeamColor) -- adding command handler
```

</section>
Author: NeonBlack

See Also
--------
