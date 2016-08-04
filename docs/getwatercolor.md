This function returns the water color of the GTA world.

**Note:** The server can only return the water color, if it has actually been set by script.

Syntax
------

``` lua
int, int, int, int getWaterColor ( )
```

### Returns

Returns 4 [ints](/docs/int.md "wikilink"), indicating the color of the water. (RGBA)

Example
-------

These two examples adds the command *watercolor* which get water color(RGBA) and show in chat.

<section name="Client" class="client" show="true">
``` lua
function waterColor ()
    local r,g,b,a = getWaterColor ()
    if ( r and g and b and a ) then -- If color is true
          -- Output of the value of the water color to the chat
        outputChatBox ( "The color of water is: "..math.ceil(r)..", "..math.ceil(g)..", "..math.ceil(b)..", "..math.ceil(a).."", r, g, b )
    else
          -- Notify the player if the value of the colors is false
        outputChatBox ( "Failed to get the color of water!" )
    end
end
  -- Add command handler for the function
addCommandHandler("watercolor", waterColor )
```

</section>
<section name="Server" class="server" show="true">
``` lua
function waterColor ()
    local r,g,b,a = getWaterColor ()
    if ( r and g and b and a ) then -- If color is true
          -- Output of the value of the water color to the chat
        outputChatBox ( "The color of water is: "..math.ceil(r)..", "..math.ceil(g)..", "..math.ceil(b)..", "..math.ceil(a).."", getRootElement(), r, g, b )
    else
          -- Notify the player if the value of the colors is false
        outputChatBox ( "Failed to get the color of water!" )
    end
end
  -- Add command handler for the function
addCommandHandler("watercolor", waterColor )
```

</section>
See Also
--------
