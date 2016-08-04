This function sets the maximum [FPS (Frames per second)](http://en.wikipedia.org/wiki/Frame_rate) that players on the server can run their game at.

Syntax
------

``` lua
bool setFPSLimit ( int fpsLimit )         
```

### Required Arguments

-   **fpsLimit:** An integer value representing the maximum FPS. This value may be between **25** and **100** FPS. You can also pass **0** or *false*, in which case the FPS limit will be the one set in the client settings (by default, 100 FPS). It is also recommended to set a conservative FPS limit (between 30-60), because high FPS can break some GTA internal calculations. The most obvious problems which occur with high FPS are a slower swimming and the impossibility to move sideways while aiming certain weapons. Also, driving is slightly affected.

### Returns

Returns *true* if successful, or *false* if it was not possible to set the limit or an invalid value was passed.

Example
-------

This command sets the fps limit in a command handler.

<section name="Server" class="server" show="true">
``` lua
function fpsFunction( player, command, limit ) -- First define the function
  if hasObjectPermissionTo ( player, "function.setFPSLimit" ) and limit then 
    -- If the player has permission to set FPS limit and limit is submitted...
    setFPSLimit ( limit ) -- Set the fps.
  end
end 

addCommandHandler ( "setfps", fpsFunction ) -- Attach the setfps command to fpsFunction function.
```

</section>
See Also
--------

[pl:setFPSLimit](/docs/pl:setFPSLimit.md "wikilink") [ru:setFPSLimit](/ru:setFPSLimit.md "wikilink")
