Removes an existing key bind from the specified player.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool unbindKey ( player thePlayer, string key, string keyState, string command )
```

``` lua
bool unbindKey ( player thePlayer, string key, [ string keyState, function handler  ] )
```

### Required Arguments

-   **thePlayer:** The player you wish to unbind the key of.
-   **key:** The key you wish to unbind. See [Key names](/docs/Key_names.md "wikilink") for a list of valid key names.
-   **keyState:** Can be either:
    -   **“up”:** If the bound key triggered a function when the key was released
    -   **“down”:** If the bound key triggered a function when the key was pressed
    -   **“both”:** If the bound key triggered a function when the key was pressed and released
-   **command :** (Syntax 1) The command you wish to unbind.

### Optional Arguments

-   **keyState:** is optional in Syntax 2.
-   **handler:** (Syntax 2) The function you wish to unbind.

Note: If you do not specify *handler*, any instances of *key* being bound will be unbound, whatever function they are bound to.

### Returns

Returns *'true* if the key was unbound, *false* if it was not previously bound or invalid arguments were passed to the function.

</section>
<section name="Client" class="client" show="true">
``` lua
bool unbindKey ( string key, string keyState, string command )
```

``` lua
bool unbindKey ( string key, [ string keyState, function handler ] )
```

### Required Arguments

-   **key:** The key you wish to unbind. See [Key names](/docs/Key_names.md "wikilink") for a list of valid key names.
-   **keyState:** Can be either:
    -   **“up”:** If the bound key triggered a function when the key was released
    -   **“down”:** If the bound key triggered a function when the key was pressed
    -   **“both”:** If the bound key triggered a function when the key was pressed and released
-   **command :** (Syntax 1) The command you wish to unbind.

### Optional Arguments

-   **keyState:** is optional in Syntax 2.
-   **handler:** (Syntax 2) The function you wish to unbind.

Note: If you do not specify *handler*, any instances of *key* being bound will be unbound, whatever function they are bound to.

### Returns

Returns *'true* if the key was unbound, *false* if it was not previously bound or invalid arguments were passed to the function.

</section>
Example
-------

<section name="Server" class="server" show="true">
This function binds the player's *F1* key to a function *goMoo* which outputs a chat message when pressed. The key is then unbound so that it can effectively only be used once per life.

``` lua
-- define the function that will be called when F1 is pressed
function goMoo( player )
    outputChatBox ( getPlayerName ( player ) .. " says Mooooooo!" )
    unbindKey ( player, "F1", "down", goMoo )   -- this function will no longer be triggered by the player, after removing the bind.
end

function playerSpawn ( )
    bindKey ( source, "F1", "down", goMoo ) -- bind the player's F1 key to the 'goMoo' function defined above
end
addEventHandler ( "onPlayerSpawn", getRootElement(), playerSpawn ) -- make the playerSpawn function be called when a player spawns
```

</section>
See Also
--------
