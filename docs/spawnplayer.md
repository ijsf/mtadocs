This function spawns the player at an arbitary point on the map.

Syntax
------

``` lua
bool spawnPlayer ( player thePlayer, float x, float y, float z, [ int rotation = 0, int skinID = 0, int interior = 0, int dimension = 0, team theTeam = getPlayerTeam(thePlayer) ] )
```

### Required Arguments

-   **thePlayer:** The player you want to spawn.
-   **x:** The x co-ordinate to spawn the player at.
-   **y:** The y co-ordinate to spawn the player at.
-   **z:** The z co-ordinate to spawn the player at.

### Optional Arguments

-   **rotation:** rotation of the player on spawn.
-   **skinID:** player's skin on spawn. [Character Skins](/docs/character_skins.md "wikilink")
-   **interior:** interior the player will spawn into. [Interior IDs](/docs/interior_ids.md "wikilink")
-   **dimension:** The ID of the [dimension](/docs/dimension.md "wikilink") that the player should be in.
-   **theTeam:** the team the player will join.

### Returns

Returns *true* if the player was spawned successfully, *false* otherwise.

Example
-------

This example spawns all the players in the middle of the game map.

``` lua
-- Get a table of all the players
players = getElementsByType ( "player" )
-- Go through every player
for playerKey, playerValue in ipairs(players) do
    -- Spawn them at the desired coordinates
    spawnPlayer ( playerValue, 0.0, 0.0, 5.0, 90.0, 0 )
end
```

This example spawns a player when he logs in.

``` lua
spawnTeam = createTeam ("Teamname", 255, 0, 0) -- Create team to spawn.
function spawnOnLogin (prevA, curA, autoLogin)
    outputChatBox ("Welcome to ...", source, 255, 0, 0, false)
    spawnPlayer (source, 0, 0, 5, 0, math.random (0,288), 0, 0, spawnTeam) -- spawns player with random skin
    fadeCamera (source, true)
    setCameraTarget (source, source)
end
addEventHandler("onPlayerLogin", getRootElement(), spawnOnLogin)
```

See Also
--------

[ru:spawnPlayer](/docs/ru-spawnplayer.md "wikilink")
