The map manager is a resource included in the MTA DM server suite. It offers commands, functions and events for the gamemodes to dynamically manage their maps. For example, when a race server needs to load different tracks for each race, instead of having all of them in the same resource as the main script, they can be stored in separate resources and then loaded simply with the “changeGamemodeMap” function when a new race starts.

Specifically, the map manager lists gamemodes/maps and manages gamemode/map loading. It applies certain map settings affecting the game world and sets ASE game type and map name rule values as well. It includes a web listing which auto updates and highlights the current mode/map combination.

A simple tutorial
-----------------

In this section we are going to continue the basic gamemode we created in the [Introduction to Scripting](/docs/Scripting_Introduction.md "wikilink"). We will add a simple map resource that only contains the spawnpoint data for the players, and load the data in the main script when the player needs to spawn.

First of all, we make a folder under /Your MTA Server/mods/deathmatch/resources/, and name it “mymap”. Then under /mymap/ directory, create a text file and name it “meta.xml”, which is required for every resource.

Enter the following codes in the *meta.xml* file:

``` xml
<meta>
   <info type="map" gamemodes="myserver"/>
   <map src="mymap.map"/>
</meta>
```

Note that this resource is “linked” to the main resource with the *gamemodes=""* tag, which contains the name of the main resource. In the *map* tag, it indicates the name of the .map file which contains the actual map data.

Now let's create another text file under /mymap/ and name it “mymap.map”, and enter the following codes:

``` xml
<map>
   <spawnpoint id="spawnpoint1" posX="1959.5487060547" posY="-1714.4613037109" posZ="18" rot="63.350006103516" model="0"/>
</map>
```

Note that “spawnpoint” is the type of the element, used in [getElementsByType](/docs/getElementsByType.md "wikilink") function; likewise, “id” is used in [getElementByID](/getElementByID.md "wikilink") function.

To load the map data, the main script needs access to the map resource itself. Now let's edit the script.lua file in “myserver” resource. Enter the following code:

``` lua
function loadMap(startedMap)
    mapRoot = getResourceRootElement(startedMap)
end

addEventHandler("onGamemodeMapStart", getRootElement(), loadMap)
```

Basically, the “onGamemodeMapStart” event gives us the handle of the map (“startedMap”), which we used to extract the handle of the resource containing the map (“mapRoot”).

With the resource handle, we can extract the spawnpoint information from it. Look at the joinHandler() function in script.lua, instead of specifying x, y and z, we can use the map data as the following:

``` lua
function joinHandler()
    local spawn = getElementsByType("spawnpoint", mapRoot)
    local x,y,z,r
    for key, value in pairs(spawn) do
        x = getElementData(value, "posX")
        y = getElementData(value, "posY")
        z = getElementData(value, "posZ")
        r = getElementData(value, "rot")
    end
    spawnPlayer(source, x, y, z)
    fadeCamera(source, true)
end
```

Now you may start the gamemode in the server console with the following command:

**gamemode myserver mymap**

Usage
-----

To use the map manager, your resources must first be marked as either gamemodes or maps.

You have to tag the **gamemode resource** with the correct type in its info tag:

``` xml
<info description="A gamemode" type="gamemode" />
```

**Map resources** also need the *type=“map”* tag, plus a *gamemodes* tag listing the gamemode resources they're compatible with in a comma-separated list *without spaces*.

``` xml
<info description="A gamemode map" type="map" gamemodes="ctv,koth" />
```

There can be only one gamemode and one gamemode map loaded at once.

Optional resource attributes
----------------------------

These attributes all go in the corresponding resource's info tag.

**name:** A friendly name for your gamemode or map, to be displayed in the start messages or map listings instead of the filename.

Commands
--------

**changemap newmap \[newgamemode\]** (changes the gamemode map to a new one, optionally changing the gamemode as well)

**changemode newgamemode \[newmap\]** (changes to a new gamemode, optionally starting a map with it)

**gamemode newgamemode \[newmap\]** (same as previous one)

**stopmode** (stops the current mode and mode map)

**stopmap** (stops the current mode map)

**maps \[gamemode\]** (lists all maps in the server, optionally all maps compatible with a gamemode)

**gamemodes** (lists all gamemodes)

Settings
--------

**\*mapmanager.color** \[hex color string\] (changes the mapmanager's output messages' color) (default: \#E1AA5A)

**\*mapmanager.messages** \[boolean\] (whether map/gm changes are enabled) (default: true)

**\*mapmanager.ASE** \[boolean\] (whether the manager will set ASE gametype / mapname) (default: true)

Exported functions
------------------

``` lua
 )
```

Changes the gamemode to a new one, optionally specifying an initial map for it (will load without a map by default).

``` lua
 )
```

Changes the GM map to a new one, optionally specifying a gamemode to change to before loading it (will load with the current gamemode by default).

``` lua
table getGamemodes ( )
```

Returns a table of all gamemode resource pointers.

``` lua
table getGamemodesCompatibleWithMap ( resource theMap )
```

Returns a table of compatible gamemode resource pointers.

``` lua
table getMaps ( )
```

Returns a table of all map resource pointers.

``` lua
 )
```

Returns a table of compatible map resource pointers. If the gamemode is left blank, it returns all maps which aren't compatible with any gamemode.

``` lua
resource getRunningGamemode ( )
```

Returns the currently running gamemode's resource pointer.

``` lua
resource getRunningGamemodeMap ( )
```

Returns the currently running GM map's resource pointer.

``` lua
bool isGamemode ( resource theGamemode )
```

Determines if a resource is a gamemode or not.

``` lua
bool isGamemodeCompatibleWithMap ( resource theGamemode, resource theMap )
```

Determines if a gamemode is compatible with a map or not.

``` lua
bool isMap ( resource theMap )
```

Determines if a resource is a map or not.

``` lua
bool isMapCompatibleWithGamemode ( resource theMap, resource theGamemode )
```

Determines if a map is compatible with a gamemode or not.

``` lua
bool stopGamemode ( )
```

Stops the current gamemode and its map.

``` lua
bool stopGamemodeMap ( )
```

Stop the current GM map. Determines if a map is compatible with a gamemode or not.

Fired events
------------

*(For all these events, “source” is the resource's root element.)*

``` lua
onGamemodeStart ( resource startedGamemode )
```

Fired before a gamemode starts.

``` lua
onGamemodeStop ( resource stoppedGamemode )
```

Fired before a gamemode is stopped.

``` lua
onGamemodeMapStart ( resource startedMap )
```

Fired before a GM map starts.

``` lua
onGamemodeMapStop ( resource stoppedMap )
```

Fired before a GM map is stopped.

Supported map settings
----------------------

The following settings from the [registry](/docs/settings_system.md "wikilink") are applied by the map manager when a map is started:
**gamespeed** \[number\]: The map's game speed.
**gravity** \[number\]: The map's gravity.
**time** \[string of the form **hh:mm**\]: The map's time.
**weather** \[number\]: The map's weather ID.
**waveheight** \[number\]: The map's wave height.
**locked\_time** \[boolean\]: Whether the set time will be frozen by the manager or not.
**minplayers** \[number\]: The required minimum number of players to start the map.
**maxplayers** \[number\]: The allowed maximum number of players to start the map.

[it:Map manager](/docs/it:Map_manager.md "wikilink") [ru:<Resource:Mapmanager>](/ru:Resource:Mapmanager.md "wikilink")
