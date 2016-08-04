This function returns the specified ped's skin.

Syntax
------

``` lua
int getPedSkin ( ped thePed )
```

### Required Arguments

-   **thePed**: The ped whose skin ID you want to retrieve.

### Returns

Returns an [int](/docs/int.md "wikilink") indicating which skin the ped has. See [Character Skins](/docs/character_skins.md "wikilink").

Example
-------

This example adds a “skin” command in console, which tells the player his/her skin.

``` lua
function checkSkin ( commandName )
    outputChatBox ( "Your skin ID is: " .. getPedSkin ( getLocalPlayer() ) )
end
addCommandHandler ( "skin", checkSkin )
```

See Also
--------
