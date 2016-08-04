This function changes the skin of a ped.

Syntax
------

``` lua
bool setPedSkin ( ped thePed, int skinID )
```

### Required Arguments

-   **thePed:** The [ped](/ped.md "wikilink") whose model will be changed.
-   **skinID:** A GTASA player model (skin) ID. See [Character Skins](/Character_Skins.md "wikilink").

Example
-------

<section show="true" name="Server" class="server">
This example sets a players skin to the cop skin when they spawn.

``` lua
function setCopSkin ()
    setPedSkin ( source, 280 )
    outputChatBox ( "You are now a cop.", source, 255, 0, 0 )
end
addEventHandler ( "onPlayerSpawn", getRootElement(), setCopSkin )
```

</section>
See Also
--------
