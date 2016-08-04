Resources are a key part of MTA. A resource is essentially a folder or zip file that contains a collection of files, plus a meta file that describes to the server how the resource should be loaded and what files it does contain. A resource can be seen as being partly equivalent to a program running in an operating system - it can be started and stopped, and multiple resources can run at once.

Everything that has to do with scripting happens in resources, what a resource does defines if it is a gamemode, a map or anything else. MTA comes with resources that you can optionally use in your gamemodes, such as maplimits to keep playings within a playing area or deathpickups to create weapon pickups.

Creating a working script
-------------------------

We will first learn how to make a basic script that lets the player walk around in the city, step by step.

### Where are all the scripts?

Let's take a look at the script's file structure. Go to your MTA Server folder, and follow the path below:

`   server/mods/deathmatch/resources/`

You will see a lot of .zip files, which are the packaged sample scripts shipped with MTA. Each file is a “resource”, and they will all be unzipped and loaded by the server when it starts. To create your own resource, simply make a folder with your preferred name. We'll use “myserver” for this tutorial.

Now you should be under this directory:

`   server/mods/deathmatch/resources/myserver/`

### Identifying your resource

In order to let the server know what's in the resource, a *meta.xml* file must be created to list the resource's content. It must be located in the resource's root directory, which is the “myserver” folder in our case. So create a text file and name it “meta.xml”, and open it with notepad.

Enter the following codes in the *meta.xml* file:

``` xml
<meta>
     <info author="YourName" type="gamemode" name="My Server" description="My first MTA server" />
     <script src="script.lua" />
</meta>
```

In the *<info />* tag, there's a “type” field which indicates that the resource is a *gamemode* instead of a regular include or a *map*, which will be explained later. A gamemode is what you need to make a stand-alone server.

The ''

<script />
'' tag indicates the script files contained in the resource, which we will create next.

### Creating a simple script

Note that in the ''

<script />
'' tag above, the .lua file is not under another directory. Therefore we'll create the file in the same folder as meta.xml. Now you can copy and paste the following code into script.lua:

``` lua
local spawnX, spawnY, spawnZ = 1959.55, -1714.46, 10
function joinHandler()
    spawnPlayer(source, spawnX, spawnY, spawnZ)
    fadeCamera(source, true)
    setCameraTarget(source, source)
    outputChatBox("Welcome to My Server", source)
end
addEventHandler("onPlayerJoin", getRootElement(), joinHandler)
```

The script will spawn you at the coordinate (x, y, z) specified above, when you join the game. Note that the *fadeCamera* function must be used or the screen will be black. Also, in releases after DP2, you need to set the camera target (otherwise all the player will see is blue sky).

The **source** variable indicates who triggered the event. Since a player has joined when the code is triggered, you use this variable to look which has joined. So it'll spawn that player instead of everyone or a random person.

If we have a closer look on [addEventHandler](/docs/addeventhandler.md "wikilink"), you can see 3 things: 'onPlayerJoin', which indicates when it's triggered. getRootElement(), which shows by what/who it can be triggered. (getRootElement() is everything/everyone) And joinHandler, which indicates the function that has to be triggered after the event is triggered. Other details will be explained later in another example, now let's just run the server and try it out!

### Running the script

To get the server started, simply run the executable under the server/ directory. A list of server stats will be shown first; note the port number, which you'll need when joining the game. Then the server loads all the resources under the mods/deathmatch/resources/ directory, and then “ready to accept connections!”

Before you connect to the server, you must run the gamemode. Type “start myserver” and press Enter. The server will start the gamemode you just created, and will also show any errors and warnings from this point on. Now you can start the MTA client, and “Quick Connect” using the IP address of your server and the port number you saw earlier. If all goes well, after a few seconds your character will be walking on the streets of Los Santos.

Next we'll add a command to your script that players can use to spawn a vehicle beside their position. You may skip it and check out more advanced scripting with the [Map Manager](/docs/map_manager.md "wikilink"), which continues this tutorial. Another branch from this tutorial is [Introduction to Scripting GUI](/docs/introduction_to_scripting_gui.md "wikilink"), you may follow it to see how Graphical User Interface in MTA is drawn and scripted.

Creating a simple command
-------------------------

Let's go back to the content of the *script.lua* file. As mentioned above, we want to provide a command to create a vehicle beside your current position in the game. Firstly we need to create a function we want to call and a command handler that creates the command the player will be able to enter in the console.

``` lua
-- create the function the command handler calls, with the arguments: thePlayer, command, vehicleModel
function createVehicleForPlayer(thePlayer, command, vehicleModel)
   -- create a vehicle and stuff
end

-- create a command handler
addCommandHandler("createvehicle", createVehicleForPlayer)
```

*Note: Function names are clickable in code examples on the wiki and linked to the functions' documentation.*

#### About command handlers

The first argument of [addCommandHandler](/docs/addcommandhandler.md "wikilink") is the name of the command the player will be able to enter, the second argument is the function this will call, in this case *createVehicleForPlayer*.

If you have already experience in scripting, you will know that you call a function like this:

``` lua
functionName(argument1, argument2, argument3, ..)
```

``` lua
functionName(thePlayer, commandName, argument3, ..)
```

If we have a closer look on the lower example above, we can see argument1 is thePlayer and argument2 the commandName. thePlayer is simply the one who typed the command, so whatever you call it, the variable will contain the player who activated the command. commandName is simply the command they typed. So if they typed "/greet", this argument will contain “greet”. Argument 3 is something extra the player typed, you'll learn it a little bit further in the tutorial. Never forget that the first 2 arguments are standard arguments, but you can name them to anything you want.

We called the [addCommandHandler](/docs/addcommandhandler.md "wikilink") function this way already and since *createVehicleForPlayer* is a function too, it can be called that way as well. But we are using a command handler for that, which calls it in a similiar manner, internally.

For example: Someone types “createvehicle 468” ingame in the console to spawn a Sanchez, the command handler calls the createVehicleForPlayer function, as **if** we would have this line of code in the script:

``` lua
createVehicleForPlayer(thePlayer,"createvehicle","468") -- thePlayer is the player element of the player who entered the command
```

As we can see, it provides several parameters: the player who called the command, the command he entered and whatever text he had after that, in this case “468” as vehicle id for the Sanchez. The first two parameters are the same with all command handlers, which you can read on the [addEventHandler](/docs/addeventhandler.md "wikilink") page. For this fact, you always have to define at least those two parameters to use any after that (for example to process text that was entered after the command, like in our example the vehicle model id).

*Note: You have to add the command handler AFTER you defined the handler function, else it can't find it. The order of execution matters.*

#### Writing the function

In order to fill the function we created, we need to think about what we have to do:

-   Get the players position, so we know where to spawn the vehicle (we want it to appear right beside the player)
-   Calculate the position we want to spawn the vehicle at (we don't want it to appear in the player)
-   Spawn the vehicle
-   Check if it has been spawned successfully, or output a message

In order to achieve our goals, we have to use several functions. To find function we need to use, we should visit the [Server Functions List](/docs/scripting_functions.md "wikilink"). First we need a function to get the players position. Since players are Elements, we first jump to the **Element functions** where we find the [getElementPosition](/docs/getelementposition.md "wikilink") function. By clicking on the function name in the list, you get to the function description. There we can see the syntax, what it returns and usually an example. The syntax shows us what arguments we can or have to submit.

For [getElementPosition](/docs/getelementposition.md "wikilink"), the syntax is:

``` lua
float, float, float getElementPosition ( element theElement )
```

The three *float* in front of the function name are the return type. In this case it means the function returns three floating point numbers. (x, y and z) Within the parentheses, you can see what arguments you have to submit. In this case only the element whose position you want to get, which is the player in our example.

``` lua
function createVehicleForPlayer(thePlayer, command, vehicleModel)
    -- get the position and put it in the x,y,z variables
    -- (local means, the variables only exist in the current scope, in this case, the function)
    local x,y,z = getElementPosition(thePlayer)
end
```

Next we want to ensure that the vehicle won't spawn directly in the player, so we add a few units to the *x* variable, which will make it spawn east from the player.

``` lua
function createVehicleForPlayer(thePlayer, command, vehicleModel)
    local x,y,z = getElementPosition(thePlayer) -- get the position of the player
    x = x + 5 -- add 5 units to the x position
end
```

Now we need another function, one to spawn a vehicle. We once again search for it on the [Server Functions List](/docs/scripting_functions.md "wikilink"), this time - since we are talking about vehicles - in the **Vehicle functions** section, where we will choose [createVehicle](/docs/createvehicle.md "wikilink"). In this function's syntax, we only have one return type (which is more common), a vehicle element that points to the vehicle we just created. Also, we see that some arguments are enclosed within \[ \] which means that those are optional.

We already have all arguments we need for [createVehicle](/docs/createvehicle.md "wikilink") in our function: The position we just calculated in the *x,y,z* variables and the model id that we provided through the command (“createvehicle 468”) and can access in the function as *vehicleModel* variable.

``` lua
function createVehicleForPlayer(thePlayer, command, vehicleModel)
    local x,y,z = getElementPosition(thePlayer) -- get the position of the player
    x = x + 5 -- add 5 units to the x position
    -- create the vehicle and store the returned vehicle element in the ''createdVehicle'' variable
    local createdVehicle = createVehicle(tonumber(vehicleModel),x,y,z)
end
```

Of course this code can be improved in many ways, but at least we want to add a check whether the vehicle was created successfully or not. As we can read on the [createVehicle](/docs/createvehicle.md "wikilink") page under **Returns**, the function returns *false* when it was unable to create the vehicle. Thus, we check the value of the *createVehicle* variable.

Now we have our complete script:

``` lua
function createVehicleForPlayer(thePlayer, command, vehicleModel)
    local x,y,z = getElementPosition(thePlayer) -- get the position of the player
    x = x + 5 -- add 5 units to the x position
    local createdVehicle = createVehicle(tonumber(vehicleModel),x,y,z)
    -- check if the return value was ''false''
    if (createdVehicle == false) then
        -- if so, output a message to the chatbox, but only to this player.
        outputChatBox("Failed to create vehicle.",thePlayer)
    end
end
addCommandHandler("createvehicle", createVehicleForPlayer)
```

As you can see, we introduced another function with [outputChatBox](/docs/outputchatbox.md "wikilink"). By now, you should be able to explore the function's documentation page yourself. For more advanced scripting, please check out the [Map Manager](/docs/map_manager.md "wikilink").

What you need to know
---------------------

You already read some things about resources, command handlers and finding functions in the documentation in the first paragraph, but there is much more to learn. This section will give you a rather short overview over some of these things, while linking to related pages if possible.

### Clientside and Serverside scripts

You may have already noticed these or similiar terms (Server/Client) somewhere on this wiki, mostly in conjunction with functions. MTA not only supports scripts that run on the server and provide commands (like the one we wrote above) or other features, but also scripts that run on the MTA client the players use to connect to the server. The reason for this is, that some features MTA provides have to be clientside (like a GUI - Graphical User Interface), others should be because they work better and still others are better off to be serverside or just don't work clientside.

Most scripts you will make (gamemodes, maps) will probably be serverside, like the one we wrote in the first section. If you run into something that can't be solved serverside, you will probably have to make it clientside. For a clientside script for example, you would create a ordinary script file (for example called *client.lua*) and specify it in the meta.xml, like this:

``` xml
<script src="client.lua" type="client" />
```

The *type* attribute defaults to 'server', so you only need to specify it for clientside scripts. When you do this, the clientside script will be downloaded to the player's computer once he connects to the server. Read more about [Client side scripts](/docs/client_side_scripts.md "wikilink").

### More complex resources

The previous section showed briefly how to add clientside scripts to the resource, but there is also much more possible. As mentioned at the very top of this page, resources can be pretty much everything. Their purpose is defined by what they do. Let's have some theoretical resources, by looking at the files it contains, the *meta.xml* and what they might do:

#### First example - A utility script

``` xml
/admin_commands
    /meta.xml
    /commands.lua
    /client.lua
```

``` xml
<meta>
    <info author="Someguy" description="admin commands" />
    <script src="commands.lua" />
    <script src="client.lua" type="client" />
</meta>
```

-   The *commands.lua* provides some admin commands, like banning a player, muting or something else that can be used to admin the server
-   The *client.lua* provides a GUI to be able to perform the mentioned actions easily

This example might be running all the time (maybe even auto-started when the server starts) as it's useful during the whole gaming experience and also wont interfere with the gameplay, unless an admin decides to take some action of course.

#### Second example - A gamemode

``` xml
/counterstrike
    /meta.xml
    /counterstrike.lua
    /buymenu.lua
```

``` xml
<meta>
    <info author="Someguy" description="Counterstrike remake" type="gamemode" />
    <script src="counterstrike.lua" />
    <script src="buymenu.lua" type="client" />
</meta>
```

-   The *counterstrike.lua* contains similiar to the following features:
    -   Let players choose their team and spawn them
    -   Provide them with weapons, targets and instructions (maybe read from a Map, see below)
    -   Define the game's rules, e.g. when does the round end, what happens when a player dies
    -   .. and maybe some more
-   The *buymenu.lua* is a clientside script and creates a menu to buy weapons

This example can be called a gamemode, since it not only intereferes with the gameplay, but actually defines the rules of it. The *type* attribute indicates that this example works with the [Map manager](/docs/map_manager.md "wikilink"), yet another resource that was written by the QA Team to manage gamemodes and map loading. It is highly recommended that you base your gamemodes on the techniques it provides.

This also means that the gamemode probably won't run without a map. Gamemodes should always be as generic as possible. An example for a map is stated in the next example.

#### Third example - A Map

``` xml
/cs-airport
    /meta.xml
    /airport.map
    /airport.lua
```

``` xml
<meta>
    <info author="Someguy" description="Counterstrike airport map" type="map" gamemodes="counterstrike" />
    <map src="airport.map" />
    <script src="airport.lua" />
</meta>
```

-   The *airport.map* in a XML file that provides information about the map to the gamemode, these may include:
    -   Where the players should spawn, with what weapons, what teams there are
    -   What the targets are
    -   Weather, World Time, Timelimit
    -   Provide vehicles
-   The *airport.lua* might contain map-specific features, that may include:
    -   Opening some door/make something explode when something specific happens
    -   Create or move some custom objects, or manipulate objects that are created through the .map file
    -   .. anything else map-specific you can think of

As you can see, the *type* attribute changed to 'map', telling the [Map manager](/docs/map_manager.md "wikilink") that this resource is a map, while the *gamemodes* attribute tells it for which gamemodes this map is valid, in this case the gamemode from the above example. What may come as a surprise is that there is also a script in the Map resource. Of course this is not necessarily needed in a map, but opens a wide range of possibilities for map makers to create their own world within the rules of the gamemode they create it for.

The *airport.map* file might look similiar to this:

``` xml
<map mode="deathmatch" version="1.0">
    <terrorists>
        <spawnpoint posX="2332.23" posY="-12232.33" posZ="4.42223" skins="23-40" />
    </terrorists>
    <counterterrorists>
        <spawnpoint posX="2334.23443" posY="-12300.233" posZ="10.2344" skins="40-50" />
    </counterterrorists>

    <bomb posX="23342.23" posY="" posZ="" />
    
    <vehicle posX="" posY="" posZ="" model="602" /> 
    <vehicle posX="" posY="" posZ="" model="603" /> 
</map>
```

When a gamemode is started with a map, the map resources is automatically started by the mapmanager and the information it contains can be read by the gamemode resource. When the map changes, the current map resource is stopped and the next map resource is started. For a more in-depth explanation and examples of how map resources are utilized in the main script, please visit the [Writing Gamemodes](/docs/writing_gamemodes.md "wikilink") page.

### Events

[Events](/docs/event.md "wikilink") are the way MTA tells scripts about things that happen. For example when a player dies, the [onPlayerWasted](/docs/onplayerwasted.md "wikilink") event is triggered. In order to perform any actions when a player dies, you have to prepare yourself similiar to adding a command handler, as shown in [the first chapter](/docs/#writing_the_script.md "wikilink").

This example will output a message with the name of the player who died:

``` lua
function playerDied(totalAmmo, killer, killerWeapon, bodypart)
    outputChatBox(getPlayerName(source).." died!")
end
addEventHandler("onPlayerWasted",getRootElement(),playerDied)
```

Instead of showing what arguments are needed, the documentation page for Events shows what parameters are passed to the handler function, similiar to the way a [command handler](/docs/#about_command_handlers.md "wikilink") does, just that it is different from event to event. Another important point is the *source* variable, that exists in handler functions. It doesn't have to be added to the parameter list of the function, but it still exists. It has a different value from event to event, for player events (as in the example above) it is the player element. As another example, you can take a look at the basic spawning player script in the first section to get an idea how *source* is used.

Where to go from here
---------------------

You should now be familiar with the most basic aspects of MTA scripting and also a bit with the documentation. The [Main Page](/docs/main_page.md "wikilink") provides you with links to more information, Tutorials and References that allow a deeper look into the topics you desire to learn about. **See also:**

-   [OOP Scripting Introduction](/docs/oop_introduction.md "wikilink")
-   [Advanced Topics](/docs/advanced_topics.md "wikilink")
-   [Script security](/docs/script_security.md "wikilink")
-   [Scripting Introduction Urdu](/docs/scripting_introduction_urdu.md "wikilink")

[es:Introducción a la Programación](/docs/es-introducción_a_la_programación.md "wikilink") [it:Introduzione allo scripting](/docs/it-introduzione_allo_scripting.md "wikilink") [nl:Scripting\_introductie](/docs/nl-scripting_introductie.md "wikilink") [pt-br:Introdução ao Scripting](/docs/pt-br-introdução_ao_scripting.md "wikilink") [ru:Scripting Introduction](/docs/ru-scripting_introduction.md "wikilink") [ar:مقدمه\_في\_البرمجه](/docs/ar-مقدمه_في_البرمجه.md "wikilink") [zh-cn:脚本编写介绍](/docs/zh-cn-脚本编写介绍.md "wikilink") [Category:Tutorials](/docs/category-tutorials.md "wikilink")
