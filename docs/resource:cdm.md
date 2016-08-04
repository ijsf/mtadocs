Classic DeathMatch is a gamemode that imitates the gameplay of MTA:VC. Before spawning the player is given the choice to select a class/team, and after spawning he's allowed to do whatever he wants, unless the map loaded limits him or instructs him otherwise.

Ingame keys
-----------

Left/Right - used to scroll through teams/classes while in spawnscreen.
Enter - used to confirm a team/class selection from the spawnscreen.
I - used to show vehicles that are close to the player.

Usage
-----

Syntax:

``` lua
<team name="" red="" green="" blue="">
    <camera lookX="" lookY="" lookZ="" posX="" posY="" posZ=""/>
    <weapon model="" ammo=""/>
    <skin model=""/>
    <spawnpoint posX="" posY="" posZ="" rot=""/>
</team>
```

When making a CDM map, one must define at least two teams, and each team must have a name, and it is optional to also give the teams colors (if none specified, defaults to white).
Inside each team there are a few definable things-

-   Camera - this is used for the camera on the spawnscreen when the team is selected. lookX/Y/Z refer to the position the camera would 'look' at, posX/Y/Z refers to the cameras position. Not specifying a camera or specifying it wrong would result in defaulting the camera to 0, 0, 0, 0, 0, 0. Note: only the first <camera> data in each team would be read.
-   Weapons - this is used as to give players weapons that their team/class receives on spawn. model refers to the weapon ID, ammo refers to how much ammo of the weapon will the player spawn with. While not specifying weapons is alright, specifying them wrong would result in an error and the map would not load. You can specify as many weapons as you wish.
-   Skins - this is used for players spawning skins. The skin they will spawn with is picked randomly from the list of skins in the current team. model refers to the skin ID. While not specifying skins would result in all players of this teams spawning with the CJ skin, specifying them wrong would result in an error and the map would not load. You can specify as many skins as you wish.
-   Spawnpoints - this is to determinate where the players would spawn. The spawnpoint the player would spawn at is randomly picked from the list of spawnpoints in the current team. posX/Y/Z refers to the spawnpoints position, rot refers to the spawning rotation. You must specify at least one spawnpoint per team, as if you specify less than one or specify a spawnpoint wrong will result in an error and the map would not load.
