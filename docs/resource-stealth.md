Stealth is a team elimination based gamemode that contains elements from counterstrike, splinter-cell, urban terror, and many original ideas thrown in. Players are encouraged to be stealthy in order to not reveal their location, and work with teammates using strategy and teamwork to win.

Gameplay
========

When a map starts, players are prompted to select a team. When the round begins, players are given a menu to select their weapons and gear. If a player takes too long to select their team or their gear, they will sit out the round. Once the player hits okay on the menu, they spawn as either a spy or a mercenary along with their teammates. The round is over when a team is eliminated or the timer runs out. The team with the most living players at the end of the round wins.

Gadgets
=======

Players are given several options to choose as their gadget. the default button to activate it is “R”. Most gadgets have limited uses. The icon next to the Sound bar shows which is the current gadget and how many uses it has left if there is a limit.

-   **CLOAK** Makes the player nearly invisible for a short period of time, allowing them to bypass proximity mines and sneak by players.
-   **RADAR BURST** Reveals all the living players exact locations at the time of the gadgets activation.
-   **PROX MINE** A player can crouch to place a mine that explodes when a member of the opposite team gets too close.
-   **GOGGLES** A player can use the gadget button to toggle between infrared and night vision while holding the goggles in your hand. The goggles counteract any cloaking from other players and reveal locations of Prox mines and Cameras while in Night vision mode, and player positions while in infrared mode.
-   **CAMERA** Pressing the gadget button while facing a wall places a camera. Pressing it again while standing away from it will activate the camera view. Use the arrow keys to moves the cameras angle around. Press fire while in Camera view to drop a Smoke grenade from the camera. You can also pick up your own camera by approaching it and pressing the gadget button again so you can place the camera elsewhere.
-   **ARMOR** Gives extra protection, as well as prevents headshots or legshot limping for as long as there is armor left
-   **SHIELD** Press the gadget button to hold up a bulletproof riot shield.

Sound
=====

A sound indication bar appears above the radar in the lower left corner of a players screen. Whenever a player does a task that creates noise, it pushes the sound level up. The sound level gradually fades back to zero. While there is sound indicated on the soundbar, a players nametag is shown, possibly revealing his/her location, as well as a blip shows on radar indicating the noisy player's location. In order to move about undetected players should operate as stealthily and methodically as possible.

Headshots and limping
=====================

If a player is shot in the head, it results in an instant kill. A shot in either leg will result in that player limping the rest of the round, restricting mobility.

Making a stealth map
====================

Stealth is compatible with mapmanager, making it easy to design your own maps. There are a few things that you need to add in order to make your map compatible with stealth.

#### TEAM SPAWNS

The spawns themselves use the default syntax, but they must be placed within a team option, with ids the specify their team. The skins will be ignored when spawning in stealth, as they are specific. Heres and example:

``` xml
<team1 id="mercspawns">
    <spawnpoint id="team1" posX="2514.339844" posY="2766.402832" posZ="11.480690" rot="90" skin="285"/>
    <spawnpoint id="team1" posX="2514.339844" posY="2763.402832" posZ="11.480690" rot="90" skin="285"/>
    <spawnpoint id="team1" posX="2514.339844" posY="2769.402832" posZ="11.480690" rot="90" skin="285"/>
</team1>

<team2 id="spyspawns">
    <spawnpoint id="team2" posX="2740.757813" posY="2786.512939" posZ="11.480690" rot="90" skin="163"/>
    <spawnpoint id="team2" posX="2740.757813" posY="2783.512939" posZ="11.480690" rot="90" skin="163"/>
    <spawnpoint id="team2" posX="2740.757813" posY="2789.512939" posZ="11.480690" rot="90" skin="163"/>
</team2>
```

#### CAMERA

A camera angle that the player will view between rounds and during menu selection. This must be placed in or near the actual gameplay area.

``` xml
<camera posX="#" posY="#" posZ="#" targetX="#" targetY="#" targetZ="#"/>
```

#### MAP SETTINGS

The time and other options are always reset at the beginning of a round. Stealth is compatible with the standard settings feature used by Map Manager

#### RENEW

If you have destructible object that you want to respawn at the beginning of every round, include this in your object code: renew=“1” for example:

``` xml
<object name="ladder" posX="2590.7119" posY="2802.854" posZ="11.288" rotX="-1.575000" rotY="0.000000" rotZ="-0.135000" model="1428" renew="1" />
```

A stealth map should have many routes to get to different areas and should challenge the player to stay quiet A good balance that allows people to be sneaky but challenges them to do so is perfect. for example, a player could quietly take a long slope that puts them in harms way, or jump up onto an edge, creating some noise.

#### RESTRICTED OBJECT

Stealth uses a custom object for the riot shield that replaces model\# 1631 (formerly a boat ramp) So using that particular model ingame will result in a shield in its place.

Credits
=======

Concept and design by Slothman, Scripting by Slothman and Talidan, Shield model by Johnline, LOTS of help from the whole QA team and the MTA team. [Category:Resource](/docs/category:resource.md "wikilink")

[ru:<Resource:Stealth>](/docs/ru:resource:stealth.md "wikilink")
