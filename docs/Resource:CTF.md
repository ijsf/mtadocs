Capture the Flag is a team based gamemode. Players capture enemy teams flags and return them to their own to gain points. The team with the most points by the end of the round wins.

Ingame keys
-----------

Left/Right - used to scroll through teams while in spawnscreen.
Enter - used to confirm a team selection from the spawnscreen.
Note: spawnscreen might be disabled on some maps.

Usage
-----

Syntax:

``` lua
<team name="" colorR="" colorG="" colorB="">
    <flag name="" posX="" posY="" posZ="" />
    <spawnpoint posX="" posY="" posZ="" rot="" model="" />
</team>
```

When making a CTF map, one must define at least two teams.
Inside each team there are a few definable things-

-   Flags - used to define a flag. Name refers to the flags name, and posX/Y/Z refers to the flags position. Each team must have at least one flag.
-   -   Spawnpoints - this is to determinate where the players would spawn. The spawnpoint the player would spawn at is randomly picked from the list of spawnpoints in the current team. posX/Y/Z refers to the spawnpoints position, rot refers to the spawning rotation. You must specify at least one spawnpoint per team.

Settings
--------

Syntax:

``` lua
<settings respawnTime="" roundTime="" spawnScreen="" blips=""/>
```

-   respawnTime refers to the amount of milliseconds a player has to wait before spawning after being killed. Default is 4500.
-   roundTime refers to the amount of milliseconds a round lasts. Default is 600000.
-   spawnScreen - if the value is “on”, spawnscreen is on. Otherwise, not spawnscreen would appear.
-   blips - if the value is “all”, all player blips and flag blips would be shown; if it's “team”, only the players teams player blips and flag blips would be shown; otherwise, CTF won't show blips.
