Assault is an objective-based team gamemode that should be similiar to Unreal Tournament's Assault. One team attacks, while the other defends. When the attacking team reached the final objective or the time runs out, the round ends and sides are switched. The team that reaches the final objective faster wins the game, if both can't reach it in the timelimit, the game ends tied.

You can easily create your own Assault maps by placing spawnareas and objectives, and of course objects, vehicles and pickups like on any other map. The default objectives are simple checkpoints you have to enter, but the exported functions allow scripters to create whole new types of objectives. See the documentation for details.

How does a game work
====================

-   Waiting for players before each new round for a certain amount of seconds or if enough players have joined
    -   Let players select their team
-   Spawn players according to their team
-   team1 has to attack and reach one or more objectives (marker), while team2 defends the objectives
    -   if team1 reached an objective, teamspawns may be at another location, according to the next objective
-   if the final objective is reached, the first round ends and team2 has to attack (on the same map)
    -   the timelimit for the second round should be the time team1 needed to reach the final objective

### Winning

-   If team2 doesn't reach the objective in the timelimit, meaning team1 was faster, team1 wins.
-   If team2 is able to reach the objective in the timelimit, meaning team2 was faster, team2 wins.
-   If team1 and team2 aren't able to reach the objective within the timelimit, game ends tied.

Creating an Assault map
=======================

Assault should work with the mapmanager, so additional maps can easily be created. It also triggers events for map specific scripts and provides functions to trigger custom objectives.

If you want to create a simple map without additional code or custom objectives, you may want to skip to the [\#Map Elements](/docs/#Map_Elements.md "wikilink").

Events/Functions
================

``` lua
onAssaultObjectiveReached ( table objectiveReached, table players )
```

Triggers when an objective is successful (when it turns red).

-   **objectiveReached:** A table with all the attributes supplied in the map file (see [Map Elements](/docs/#Objectives.md "wikilink"))
-   **players:** A table of all players that were in the marker when it was activated

``` lua
onAssaultStartRound ( team attacker )
```

Triggers when a round actually starts (player spawns), 'attacker' is the team that attacks.

-   **attacker:** A team element consisting the attacking team

``` lua
onAssaultCreateObjective ( table objectiveToCreate )
```

Triggers when a objective is created or should be created if it's a custom objective, instead of creating the marker when it would be a normal one

-   **objectiveToCreate:** A table with all the attributes supplied in the map file (see [Map Elements](/docs/#Objectives.md "wikilink"))

``` lua
onAssaultEndRound( bool conquered )
```

Triggers when the round ends (time up or base conquered)

-   **conquered:** If the attacker was successful in completing the objectives, true otherwise false.

``` lua
 )
```

Used to trigger an objective. Returns *true* if it can be triggered, *false* otherwise.

-   **objectiveId:** *(required)* The id (like defined in the .map file) of the objective.
-   **players:** A table of all players that were reponsible for activating the objective

*Please note that you have to use [Call](/docs/Call.md "wikilink") with exported functions.*

General Assault Settings
========================

**(as of version 1.1)**

These settings can be specified in Assault's *meta.xml* [settings](/docs/Settings_system.md "wikilink").

-   **teamBalance**: Defines how many more players can be in either team respectively. For example when you set it to '1' while Team Blue has 2 players and Team Red has 1 player, new players couldn't join Team Blue. If you had set it to '2' in the same situtation, one more player could join Team Blue. (*default: 1*)

Map Elements
============

To create an Assault map, all of these elements are obligatory.

General Map Settings
--------------------

**(as of version 1.1, in version 1.0 only some settings can be set in the meta.xml)**

All these settings can be specified in the *meta.xml* [settings](/docs/Settings_system.md "wikilink") or the *assaultSettings* element in the mapfile. The *meta.xml* settings will always overrule the mapfile settings.

To specifiy the settings in the *meta.xml* file, it may look like this:

``` xml
<meta>
    <info author="driver2" type="map" gamemodes="assault" />
    <map src="as-area51.map" />
    <script src="as-area51.lua" />

    <settings>
        <setting name="#author" value="driver2" />
        <setting name="#timelimit" value="300" />
        <!-- more settings.. -->
    </settings>
</meta>
```

To specifiy the settings in the mapfile, put the *assaultSettings* in your mapfile:

``` xml
<assaultSettings timelimit="(int=300)"
         finishType="(string)"  finishObjective="(string)"
         time="(time=12:00)"    weather="(int=0)"
         author="{string=''}"   description="{string=''}" />
```

#### Required Attributes

*none*

#### Optional Attributes

-   **finishObjective:** Specifies the objective (id) that has to be reached by the attackers in order to finish the round. If left empty, all objectives have to be reached.
-   **finishType:** You *can* specify the **finishType** in addition to the **finishObjective** (*in version 1.0 this is required*)
    -   **“objective”:** when a certain objective is reached
    -   **“all”:** when all objectives are reached

If there is a **timelimit**, **time**, **weather**, **author** or **description** [setting](/docs/Settings_system.md "wikilink") specified in the meta file, it will overule the attribute in this element (version 1.0)

-   **timelimit:** duration of one round in seconds *(default: 300)*
-   **time:** time hours:minutes *(default: 12:00)*
-   **weather:** weather id *(default: 0)*
-   **author:** the map author *(default: "")*
-   **description:** map description *(default: "")*
-   **defenderText:** The text that is displayed at the bottom of the screen, telling the defenders what to do. If this text is defined here, it will be set as default for the map, but can be overwritten by single objectives by specifying the according attribute in its element. *(default: “Prevent attackers from reaching their objectives!”)*
-   **attackMessage:** The message that is shown once an attacker spawns *(default: “Assault the base!”)*
-   **defendMessage:** The message that is shown once a defender spawns *(default: “Defend the base!”)*
-   **conqueredMessage:** This message replaces a part of the message that is shown when the attackers successfully reached their objectives *(default: “conquered the base”)*
    -   This messages replaces the following part enclosed by brackets (example): “Red \[conquered the base\] in 4:39”
-   **defendedMessage:** This message replaces a part of the message that is shown when the defenders successfully defended the objectives *(default: “defended the base”)*
    -   This messages replaces the following part enclosed by brackets (example): “Blue \[defended the base\]. Blue wins.”

It is recommended that you change the above messages only if the default messages make no or little sense for your map, in order to keep the messages (almost) the same for all maps.

Objectives
----------

``` xml
<objective name="(string)" description="(string)" successText="(string)" id="(string)" req="(string)"
        posX="(float)" posY="(float)" posZ="(float)" stay="{int=0}"
        forcedRespawn="{string=none}" markerType="{string=cylinder}" captureType="{string=foot}" />
```

The order of the objectives in the .map file matters. It is responsible for the order the objectives are displayed on the hud, as well as in the GUI.

#### Required Attributes

-   **posX, posY, posZ: (required)** position of the objective

#### Optional Attributes

-   **name:** the name of the objective, used for the objective list on the screen
-   **description:** may be used in the help windows and is displayed at the bottom of the screen to tell the attacker what to do
-   **successText:** shown when the objective is reached, use ~team~ as a variable for the attacker's team name
    -   *default:* Objective **name** reached
    -   If **name** and **successText** are both not given, no message at all will appear when the objective is reached
-   **id:** unique identification for the objective
-   **req:** objectives required for this objective, ids seperated by comma, e.g. req=“door,room1,room2”
-   **type:** the type of the objective
    -   **“checkpoint”:** *(default)* assault creates a checkpoint at the location, which has to be activated by the attacker by walking into it
    -   **“custom”:** assault does nothing about it except waiting for another script to trigger it (see other assault maps for how it's done)
-   **forcedRespawn**
    -   **“both”:** make all players respawn, as soon as the objective is created
    -   other values may come
-   **markerType:** defines the type of the marker used to mark the objective (see [CreateMarker](/docs/CreateMarker.md "wikilink") for details on the values)
-   **captureType:** defines how the objective can be activated
    -   **“both”:** on foot and in a vehicle
    -   **“foot”:** only while on foot
    -   **“vehicle”:** only while in a vehicle
-   **stay:** number of seconds the player needs to stay in the objective
-   **stayText:** the text that is shown above the progress bar while being in the objective
-   **defenderDescription:** This text is shown at the bottom of the screen to tell the defenders what to do *(default: the **defenderText** attribute of the [\#Assault Settings](/docs/#Assault_Settings.md "wikilink") element)*
-   **successTextForDefender:** This attribute can overwrite the **successText** attribute for defenders

Spawngroups
-----------

``` xml
<spawngroup type="(string)" req="(string)">
- put spawnareas here -
</spawngroup>
```

A spawngroup is a collection of one or several spawnareas. One of the spawnareas will be randomly selected on spawn. You can use this to let attacking players attack from different sides or to let some players spawn with different weapons for example. Always the last spawngroup (from the order in the mapfile) that meets the 'req' requirements is used to spawn players.

#### Required Attributes

-   **type:**
    -   **“attacker”:** a spawngroup for the attacking team
    -   **“defender”:** a spawngroup for the defending team

#### Optional Attributes

-   **req:** objective ids seperated by comma required for this checkpoint to work

Spawnareas
----------

``` xml
<spawnarea posX="(float)" posY="(float)" posZ="(float)" sizeX="(int=2)" sizeY="(int=2)" skins="{int,int=0}" weapons="{int,int;int,int=''}" radius="{int=2}" shape="{string=circle}" />
```

A spawnarea is a rectangle or circle in which players are spawned randomly. It is defined by one point and two size values or the radius.

#### Required Attributes

-   **posX, posY, posZ:** position

#### Optional Attributes

-   **skins:** list of skins of which one is randomly chosen, seperated by comma, range of skins seperated by hyphen (e.g. 10,14,20-24 would be 10,14,20,21,22,23,24)
-   **weapons:** weapon1,ammo1;weapon2,ammo2;weapon3,ammo3..
-   **shape**
    -   **“circle”: (default)** a circle
    -   **“rectangle”:** a rectangle
-   **sizeX, sizeY:** if shape=“rectangle”, the maximum number that will be added to the X or Y coordinate
-   **radius:** if shape=“circle”, radius of the circle

Cameras
-------

You need to define one camera of each type in a valid assault map.

``` xml
<camera type="(string)" posX="(float)" posY="(float)" posZ="(float)" targetX="(float)" targetY="(float)" targetZ="(float)" />
```

#### Required Attributes

-   **posX, posY, posZ, targetX, targetY, targetZ:** position and look at
-   **type:** defines the type of the camera, when it will be used
    -   **“spawn”:** after selecting the team and before spawning
    -   **“selectTeam”:** select Team screen
    -   **“finish”:** when the last objective is reached

#### Optional Attributes

(none)

Additional Information
----------------------

-   If you don't want a specific vehicle to be respawned by assault, set it's Elementdata item 'noRespawn' to *true* by script or add the attribute noRespawn=“1” to the element in the mapfile. Remember that it will never be automatically respawned then, so if you want to have it return to it's original place, for example after the round ends or when it is destroyed, you have to respawn it yourself.

[ru:<Resource:Assault>](/docs/ru:Resource:Assault.md "wikilink")
