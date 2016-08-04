This function returns an integer containing the ID number of the specified player's skin.

Syntax
------

``` lua
int getPlayerSkin ( player thePlayer )
```

### Required Arguments

-   **player**: The player whose skin ID you want to retrieve.

### Returns

Returns an [int](/docs/int.md "wikilink") indicating which skin the player has. See [Character Skins](/docs/character_skins.md "wikilink").

Example
-------

<section name="Server" class="server " show="true">
**Example 1:** This example spawns a player and tells him his skin

``` lua
-- Spawn a player 
if ( spawnPlayer ( myPlayer, 1000, 1000, 1000, 90, 650 ) ) then
    -- Tell the player what skin they've spawned with
    outputChatBox ( "Your skin ID is: " .. getPlayerSkin ( myPlayer ), myPlayer )
end
```

**Example 2:** This example adds a “skin” command in console, which tells the player his/her skin.

``` lua
function checkSkin ( source, commandName )
    outputChatBox ( "Your skin ID is: " .. getPlayerSkin ( source ), source )
end
addCommandHandler ( "skin", checkSkin )
```

</section>
<section name="Client" class="client" show="true">
This example adds a “skin” command in console, which tells the player his/her skin.

``` lua
function checkSkin ( commandName )
    outputChatBox ( "Your skin ID is: " .. getPlayerSkin ( getLocalPlayer() ) )
end
addCommandHandler ( "skin", checkSkin )
```

</section>
See Also
--------
