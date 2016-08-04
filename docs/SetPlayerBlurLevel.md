Sets the motion blur level on the clients screen. Accepts a value between 0 and 255.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool setPlayerBlurLevel ( player thePlayer, int level )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") whose blur level will be changed.
-   **level:** The level to set the blur to (default: 36)

</section>
<section name="Client" class="client" show="true">
``` lua
bool setBlurLevel ( int level )
```

### Required Arguments

-   **level:** The level to set the blur to (default: 36)

</section>
Example
-------

<section name="Server" class="server" show="true">
This example allows the player to set their blur level via a command

``` lua
 
function changeBlurLevel ( playerSource, command, blur )
    blur = tonumber(blur)
    if not blur or blur > 255 or blur < 0 then
        outputChatBox ( "Enter a value between 0 - 255.", playerSource )
    else
        setPlayerBlurLevel ( playerSource, blur )
        outputChatBox ( "Blur level set to: " .. blur, playerSource )
    end
end

addCommandHandler("blur", changeBlurLevel)
```

</section>
See Also
--------
