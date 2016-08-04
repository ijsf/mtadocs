Sets the interior of the local camera. Only the interior of the camera is changed, the local player stays in the interior he was in.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool setCameraInterior ( player thePlayer, int interior )
```

### Required Arguments

-   **thePlayer:** the player whose camera interior will be set.
-   **interior:** the interior to place the camera in.

</section>
<section name="Client" class="client" show="true">
``` lua
bool setCameraInterior ( int interior )
```

### Required Arguments

-   **interior:** the interior to place the camera in.

</section>
### Returns

Returns *true* if the camera's interior was changed successfully, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
<strong> This example make a command to change your cam interior to a selected one. </strong>

``` lua
function setCamInt( thePlayer, commandName, intID )
        if( intID )then -- If there is an ID
        local seted = setCameraInterior( thePlayer, intID ) -- set the interior to the camera
                if( seted )then -- If it has been changed correctly
                        outputChatBox( "Your camera's interior has been set to "..intID, thePlayer ) -- Tell to the player his new camera's interior
                else -- otherwise
                        outputChatBox( "Can't change your camera's interior...", thePlayer, 255, 0, 0 ) -- Tell him the change failed
                end
    else -- otherwise 
        outputChatBox( "Syntax: /caminterior [interiorID] ", thePlayer, 255, 0, 0 ) -- Tell him the correct syntax
    end
end
addCommandHandler( "caminterior", setCamInt )
```

</section>
<section name="Client" class="client" show="true">
<strong> This example make a command to change your cam interior to a selected one. </strong>

``` lua
function setCam(command,int)
    if (int) then
        local setInt = setCameraInterior(int)
                if (setInt) then
                        outputChatBox("Your camera's interior has been set to "..int,255,255,0)
                else
                        outputChatBox("Can't change your camera's interior...",255,0,0)
                end
    else
        outputChatBox("Syntax: /camera [interiorID] ",255,0,0)
    end
end
addCommandHandler("camera",setCam)
```

</section>
See Also
--------
