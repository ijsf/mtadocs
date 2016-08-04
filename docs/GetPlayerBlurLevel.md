This function allows you to check the current blur level of a specified [player](/player.md "wikilink").

Syntax
------

<section name="Server" class="server" show="true">
``` lua
int getPlayerBlurLevel ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") whose blur level you want to check.

### Returns

Returns the player's blur level if successful, *false* if an invalid player was given.

</section>
<section name="Client" class="client" show="true">
``` lua
int getBlurLevel ()
```

### Returns

Returns the local blur level.

</section>
Example
-------

<section name="Server" class="server" show="true">
This example adds a command *blurlevel* with which you can check your current blur level.

``` lua
function checkBlurLevel( playerSource )
    local blur = getPlayerBlurLevel( playerSource )
    if blur then
        outputChatBox( "Blur level: " .. blur, playerSource )
    end
end
addCommandHandler("blurlevel", checkBlurLevel)
```

</section>
See Also
--------
