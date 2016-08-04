This function returns a float that contains the current armor for the specified [player](/docs/player.md "wikilink").

Syntax
------

``` lua
float getPlayerArmor ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") whose armor you want to check

### Returns

A *float* with the armor, *false* if an invalid player was given.

Example
-------

This example defines a “showarmor” console command that shows the player that executes it how much armor he has.

<section name="Client" class="client" show="true">
``` lua
function showArmor ( )
    local me = getLocalPlayer ( )
    local armor = getPlayerArmor ( me )
    outputChatBox( "Your armor: " .. armor, me )
end
addCommandHandler ( "showarmor", showArmor )
```

</section>
See Also
--------
