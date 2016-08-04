Returns the interior of the local camera (independent of the interior of the local player).

Procedural
----------

### Syntax

<section name="Server" class="server" show="true">
``` lua
int getCameraInterior ( player thePlayer )
```

### Required Arguments

**thePlayer**: The player whose camera interior you want to get.

</section>
<section name="Client" class="client" show="true">
``` lua
int getCameraInterior ( )
```

</section>
Returns an *integer* indicating the camera's interior, *false* if the argument is invalid.

### Example

<section name="Server" class="server" show="true">
``` lua
function outputCameraInterior ( player, command )
    local interior = getCameraInterior ( player )
    outputChatBox ( "The camera is in the interior " .. interior, player, 255, 255, 0 )
end
addCommandHandler ( "camera", outputCameraInterior )
```

</section>
See Also
--------
