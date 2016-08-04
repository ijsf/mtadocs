This page explains some advanced things you can do with scripts, this page should probably be changed later, depending how useful it is.

Custom element types
--------------------

### Forward

One of the most powerful areas of MTA scripting is custom element types. That is, they are nothing else than new objects you add to extend GTA's world diversity. For instance, the race gamemode uses the spawnpoint and pickup elements to make player matches possible by providing spawn locations and pickups to help them during the track.

By simply defining the element type in any map file entry, MTA automatically recognizes it as a custom one when it starts. Its up to the script to decide how to deal with the information provided. In this section, we're going over the steps how to implement part of the capture-the-flag's system, but this same method can be used for many different things.

### Implemention of an imaginary flag

First of all, we can't possibly code without thinking how our system going to work first. Lets say we have an imaginary flag around the city created by an ordinary map file:

``` pua
<flag id="redFlag" name="red team flag" posX="1210.0" posY="-2241.34" posZ="18.4332" />
```

Why this way? Because it must have an ID to differ from others, a name to be displayed in the game and world position. What we just did was to outline the flag's basic information that our ctf system will require. From that point, we can start coding.

To keep things simple, we'll create a tiny resource for this tutorial, and you should already know [how to spawn a player](/Scripting_Introduction#Creating_a_simple_script.md "wikilink") and [make use of events](/Scripting_Introduction#Events.md "wikilink"). That resource *will spawn people and handle any flag element created by the current running map* and it only needs one server-side script called ctf.lua or just whatever name you want to give to it.

With the player spawn code in the script, lets add an custom event that happens when someone pick a flag up, called *onFlagPickup*. It may be defined anywhere in your script, but it should already exists if you want to use it (i.e. addEventHandler). So, our script will look like this:

``` lua
local spawnX, spawnY, spawnZ = 1959.55, -1714.46, 10
addEvent ("onFlagPickup", true) –- event added here just to ensure it can be used by hole script

function joinHandler()
    spawnPlayer(source, spawnX, spawnY, spawnZ)
    fadeCamera(source, true)
    setCameraTarget(source, source)
    outputChatBox("Welcome to My Server", source)
end

function flagPickup ( player )
    flagName = getElementData ( source, "name" )
    playerName = getPlayerName ( player )
    outputChatBox ( playerName .. " picked up the flag " .. flagName )
end

addEventHandler("onPlayerJoin", getRootElement(), joinHandler)
addEventHandler("onFlagPickup", getRootElement(), flagPickup)
```

Easy enough! We've added an event-driven function (flagPickup). To put it in another way, when the event triggers that function will output who got the flag. We also attached the event to the server root because our gamemode have to function to any flag in the server. We can optimize our script by attaching to the map root, but it requires more code and it is not the our goal yet.

The final part of the puzzle is to trigger the event when the player gets in the flag. To do this, we need to create a timer-driven function that will be used to check if a player is trying to pick it up. So we add the following code to our script:

``` lua
function flagCheckPulse ( )
    local flags = getElementsByType ( "flag" )
    local players = getElementsByType ( "player" )
    local flagPositionX, flagPositionY, flagPositionZ
    for flagKey,flagValue in ipairs(flags) do
        flagX = getElementData ( flagValue, "posX" )
        flagY = getElementData ( flagValue, "posY" )
        flagZ = getElementData ( flagValue, "posZ" )       
        for playerKey,playerValue in ipairs(players) do
            playerX, playerY, playerZ = getElementPosition ( playerValue )
            distance = getDistanceBetweenPoints3D ( flagX, flagY, flagZ, playerX, playerY, playerZ )
            if ( distance < 1) then
                triggerEvent ( "onFlagPickup", flagValue, playerValue )
            end
        end
    end
end
setTimer (flagCheckPulse,1000,0)
```

What we've done here was to create a simple gamemode which reconizes and listen to a custom element (the flag) in the server's environment (the root). To put simply, it has an abstract capture-the-flag game algorithm. In theory, it would works just great, but the flag doesn't really exists in the world space - nobody even know where it is.

I suppose you just have an meta.xml and ctf.lua in your resource. So if it runs in the server (no conflicting gamemode or errors) we can take the next step to spawn and represent our flag in GTA's world.

### Flag World Represetation

Soon...
