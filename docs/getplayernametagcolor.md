This function gets the current color of a player's name tag as RGB values. These are in the range 0-255.

Syntax
------

``` lua
int, int, int getPlayerNametagColor ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The player whose name tag RGB color values you wish to retrieve.

### Returns

Returns *red*, *green* and *blue* values if an existent player was specified, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This console command will tell the player what his tag color is. The color is composed of a red, a green and a blue component, each ranging from 0-255.

``` lua
function tagInfoCommand ( thePlayer, commandName )
    -- store the RGB data about the player who activated the command handler into the local variables r, g, b. 
    local r, g, b = getPlayerNametagColor ( thePlayer )
    -- Display the RGB values in the chatbox
    outputChatBox ( "Your tag color is: R:" .. r .. " G:" .. g .. " B:" .. b, thePlayer )
end
addCommandHandler ( "retrievetagcolor", tagInfoCommand )
```

</section>
See Also
--------
