This guide tries to outline the process of how to write a proper gamemode. If you just started with scripting for MTA, you may want to check the other scripting tutorials at the [Main Page](/Main_Page.md "wikilink") first.

Introduction
------------

A gamemode is a resource that, once started, controls all of the gameplay. This may include telling the players what to do, spawning players, creating teams, defining what the players have to do to win or to get points and much more. Examples are Race and Deathmatch.

What does “proper gamemode” mean?
---------------------------------

To put it simply, a proper gamemode is one that makes full use of MTA's .map file system. This means that the gamemode code does not have any map-specific data hardcoded in it, like positions of players or cars. Instead, the gamemode should be able to load .map files which define these data. This way the gamemode can have multiple maps; also, people can create .map files for the gamemode with MTA's map editor, which is much more convenient than writing code.

An obvious example of a “proper gamemode” is MTA:Race. It allows usermade maps with lots of possibilities within the .map file. To alter spawnpoints, objects etc., the user doesn't need to edit the gamemode itself.

### Map Files

Map files are basically XML documents with a .map extension. They define an environment to play one or more specific gamemodes in. They are however not supposed to change the rules of the game - those are defined by the gamemode.

Each element in a map corresponds to a node in the .map file. There is standard syntax for common things like spawnpoints, objects and vehicles; however, for “special”, gamemode specific information, you need to invent your own syntax.

#### Example

Let's take a Capture the Flag gamemode as an example. A map for this gamemode needs to mainly define spawnpoints and flag locations, and eventually objects and vehicles. A simplified map file could look like this:

``` xml
<map>
    <spawnpoint id="spawnpoint1" posX="1959.5487060547" posY="-1714.4613037109" posZ="877.25219726563" rot="63.350006103516" model="0"/>
    <pickup id="Armor 1" posX="1911.083984375" posY="-1658.8798828125" posZ="885.40216064453" type="armor" health="50" respawn="60000"/>
    <flag posX="1959.5487060547" posY="-1714.4613037109" posZ="877.25219726563" team="blue" />
    ...
</map>
```

Here you can see two MTA elements - a spawnpoint and a pickup. More importantly, this .map has a custom “flag” node which defines the position and color of the flag. The spawnpoint and pickup can be handled by existing external resources, custom elements have to be processed by the gamemode.

To summarize - we want mass mapper input as we saw in MTA:Race. Users should NOT have to touch the gamemode script itself at all.

#### Example of getting the .map information

As mentioned above, your gamemode needs de retrieve custom elements that are defined in a map file and process them. This is quite easy as demonstrated below.

``` lua
-- retrieve a table with all flag elements
local flagElements = getElementsByType ( "flag" )
-- loop through them
for key, value in pairs(flagElements) do
    -- get our info
    local posX = getElementData ( value, "posX" )
    local posY = getElementData ( value, "posY" )
    local posZ = getElementData ( value, "posZ" )
    local team = getElementData ( value, "team" )
    -- create an object according to the flag position
    createObject ( 1337, posX, posY, posZ )
    -- output the team that we created a base for
    outputChatBox ( "Base for team " .. team .. " created" )
end
```

The [getElementsByType](/getElementsByType.md "wikilink") function retrieves a table of all the elements of a certain type (the type corresponds to the node name in the .map file). This works for both custom types and built-in MTA types (like “vehicle” or “player”). [getElementData](/getElementData.md "wikilink") can be used to retrieve the xml attributes set in the .map file. In this simple example, an object is created at the flag's location and a message is outputted in the chatbox. In reality, you will of course need to do more during map loading, like in this case setting up collision shapes to detect players taking the flag.

Map manager
-----------

Having read the section above it should be clear that a gamemode should always consist of two parts:

-   The gamemode resource that always stays the same
-   Many different maps resources that give the gamemode map-specific information

Now instead of writing a map-loader for every single gamemode, the [Map manager](/Map_manager.md "wikilink") provides functions to load gamemodes and maps. Simply put, when you enter the correct command (for example 'gamemode ctf ctf-italy') it will start both resources 'ctf' and 'ctf-italy' while triggering an event ([onGamemodeMapStart](/onGamemodeMapStart.md "wikilink")) to tell the 'ctf' resource that a map was loaded. The 'ctf' resource can then access the information 'ctf-italy' contains and start spawning players etc.

### How to use the mapmanager

To use the mapmanager service, your gamemode resource has to be tagged as such first. More specifically you'll be setting the “type” attribute of its <info> tag to “gamemode” inside meta.xml. Also, you can set the “name” attribute to a friendly name (like “Capture the flag”) that will be shown on ASE instead of the resource name.

``` xml
<!-- meta.xml in "cowcatapult" gamemode -->
<meta>
    <info type="gamemode" name="Cow catapulting 2.0"/>
</meta>
```

If your gamemode is going to load custom maps, you should add handlers for

-   onGamemodeMapStart
-   onGamemodeMapStop (if any unloading is necessary)

These are fired when a map for your gamemode is started or stopped, and pass the map resource as a parameter. Within the handler function for these events you can extract all info you need from the resource's map files and configuration files.

#### Example

``` lua
function startCtfMap( startedMap ) -- startedMap contains a reference to the resource of the map
    local mapRoot = getResourceRootElement( startedMap )        -- get the root node of the started map
    local flagElements = getElementsByType ( "flag" , mapRoot ) -- get all flags in the map and store them in a table
    -- go on loading information like in the example above
    -- spawn players etc.
end
addEventHandler("onGamemodeMapStart", getRootElement(), startCtfMap)
```

### Making maps compatible

Maps are separate resources. This is done so no editing of the gamemode resource is ever necessary in order to create a custom map, and also allows you to pack map-specific scripts/config files with them.

To make a map compatible with your gamemode, open its resource's meta.xml and tag it as well: the “type” attribute must be set to “map”, and the “gamemodes” attribute must be a comma-separated list (no spaces) of gamemode resource names that the map works with.

``` xml
<!--map's meta.xml-->
<meta>
    <info type="map" gamemodes="cowcatapult,assault,tdm"/>
</meta>
```

Once you have everything set up, admins will use these two commands to start/stop gamemodes: /gamemode gamemodeName \[mapName\] (optional parameter allows picking an initial map, defaults to none) /changemap mapName \[gamemodeName\] (optional parameter specifies the gamemode to start the map with, defaults to the current one)

[Map manager](/Map_manager.md "wikilink") exports a few more access functions which you don't have to use, but may be useful.

What else should you do
-----------------------

There are several other resources that gamemodes should use/be compliant with.

### Helpmanager

The helpmanager is ought to be the standard interface for players when they need help. If you use the helpmanager to display your gamemode's help, every player that used helpmanager before (e.g. in other gamemodes) will immediately know how to get there. It also displays help for different resources running resources in one window, if necessary.

There are basicially two ways to use the helpmanager:

-   Provide a simple text that explains how to use your gamemode
-   Request a GUI element from the helpmanager that will be displayed in its own tab in the helpmanager window and lets you add any GUI elements to it. This is the recommended way for gamemodes that need to display more complex information that needs its own GUI.

Read the [helpmanager help page](/Resource:Helpmanager.md "wikilink") for details on how to do it.

### Scoreboard

Scoreboard displays players and teams currently ingame. You add custom columns to it to provide map specific information. For example the column 'points' in the 'ctf' gamemode could represent the player's points gained through kills or captures. As usual, see the [scoreboard help page](/Resource:Dxscoreboard.md "wikilink") for more information.

### Map cycler

The map cycler controls what gamemodes and maps are played on a server. You can specifiy for example how many times in a row a map will be played until it switches to the next. To achieve this, you need to tell the map cycler when your gamemode finished (e.g. when a round ends).

[it:Scrivere una gamemode](/it:Scrivere_una_gamemode.md "wikilink") [ru:Writing Gamemodes](/ru:Writing_Gamemodes.md "wikilink") [de:Gamemodes schreiben](/de:Gamemodes_schreiben.md "wikilink") [Category:Tutorials](/Category:Tutorials.md "wikilink")
