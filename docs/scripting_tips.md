This page contains a variety of things that knowing, make life easier for MTA scripters.

General Lua
-----------

-   The *infinite loop / too long execution error* which aborts execution can be disabled with *debug.sethook(nil)*
-   Be careful when looping a table where you intend to delete multiple rows, if 2 of them are in a row the 2nd one will get skipped! You must loop the table backwards (reverse ipairs). For example: *for i = \#table, 1, -1 do*
-   Rather than having if checks inside if checks inside if checks, consider using *return* for example *if (not ready) then return false end*
-   Keep event, variable & function names short but understandable - longer names will make the file larger in size. In client files, this will increase download time.
-   Remember that 'false' boolean has a value - If you want to delete a variable or element/account data, use 'nil' instead - this will reduce memory and disk usage (minuscule optimization, only notable on larger servers)

MTA Scripting
-------------

-   Remember that 99% of the time it's a bug in your script, not an MTA bug! Don't report something to the mantis until you're absolutely certain the bug can be reproduced with a small piece of script.
-   As MTA already has so many functions and events virtually everything you want to do is already possible, as long as you're willing to do the work! You'll find better solutions to problems as there are many ways to achieve the same thing as long as you know all the functions and events.
-   If a script is getting too complicated, try putting back-end stuff in another file so the main script calls the functions in the 2nd one. For example rather than having meaningless things like *vehicleTable\[vehicle\]\[7\]* in the main file, put that in a function in the 2nd file and have the main file call a meaningfully named function so rather than seeing a useless *7* you'd see something like *getFuel* and although this might take longer to set-up you'll save time in the long run as you'll spend less time being confused when you come back to it in a weeks time to debug a problem.
-   Your client side scripts can cause desync if you're not careful, try to keep the psychical world equal with every player. For example if your script creates a client side object make sure your script will create it for everyone nearby, else people will be wondering why a player appears to be constantly floating and falling.
-   Instead of using *onClientResourceStart* or *onResourceStart* events attached to *resourceRoot* like this:

``` lua
function warnPeopleThatThisResourceStarted()
    outputChatBox("The resource " .. getResourceName(resource) .. " has just started!", 0, 255, 0)
end
addEventHandler("onClientResourceStart", resourceRoot, warnPeopleThatThisResourceStarted)
```

You can also use this outside of any function:

``` lua
outputChatBox("The resource " .. getResourceName(resource) .. " has just started!", 0, 255, 0)
```

And the result will be the same, because Lua executes every instruction in every script file of a resource when it starts.

-   string.dump produces unsigned compiled Lua code which is not allowed for security reasons. The only way to transport code now is by using the source code. e.g.:

``` lua
exampleFunction = [===[
    return param
]===]

local loadedFunction = loadstring(exampleFunction)
```

MTA Scripting - Element IDs Being Reused
----------------------------------------

-   If your script is covered in [isTimer](/docs/istimer.md "wikilink") and [isElement](/docs/iselement.md "wikilink") checks to hide debug warnings from deleted elements not being dereferenced (making the variable nil) you will regret it when that element ID or timer pointer has to be re-used by MTA in a weeks time and your script starts acting strangely and you won't have a clue why. Dereference destroyed elements and disconnected players!
-   Why would MTA reuse it in a weeks time? Everything has a userdata value whether it's a function or an element, there is a limited amount of these available meaning that eventually the server will be forced to use the same userdata value twice, as long as whatever that userdata value was for is no longer valid. This could happen within hours, weeks or even never depending on how many elements are being created and destroyed by your scripts.
-   For example if you have a race server that has 100 objects in every map and the map was changing every 5 minutes your server would go through at least 1200 an hour, 28,800 a day, 201,600 a week in userdata values, it can't keep going up and up though eventually it will have to reuse the same userdata values and as long as you're dereferencing in your scripts, it won't be a problem.

The is an example of a script which fails to dereference, because when the player quits their userdata value remains in the table, but what if in a weeks time another player joins and they get assigned the same userdata value?

``` lua

local admins = {}
local secretPasswordOnlyAdminsShouldKnow = "12345678"

function adminLogin()
    if (hasObjectPermissionTo(source, "command.ban", false)) then
        admins[source] = true
    end
end
addEventHandler("onPlayerLogin", root, adminLogin)

function cmdGetSecretPassword(plr)
    if (not admins[plr]) then
        return false
    end
    outputChatBox("The secret password is "..secretPasswordOnlyAdminsShouldKnow, plr)
end
addCommandHandler("getsecretpass", cmdGetSecretPassword)
```

Some random player who joins in a weeks time gets the same userdata value as an admin, that player can now use “getsecretpass”. Solution? De-reference on destruction!

``` lua

function onQuit()
    admins[source] = nil
end
addEventHandler("onPlayerQuit", root, onQuit)
```

Server Performance
------------------

-   Server lagging? Check [this page of debugging performance issues](/docs/debugging#debugging_performance_issues.md "wikilink")
-   Using resourceRoot in event handlers for events from clients is much more efficient than using root.
-   Try to be efficient, but if what you're doing is too time consuming or complex, is it really efficient?
-   It's much more efficient to [SetElementHealth](/docs/setelementhealth.md "wikilink") and [setElementRotation](/docs/setelementrotation.md "wikilink") on a player client side, consider a client event all your server scripts can call to set a players health.
-   Unless you have hundreds of players, don't worry about making little optimizations, check *performancebrowser* or *ipb* (ingame performancebrowser) and make sure no resource is using significantly more than the others.

Client Performance
------------------

-   The biggest cause of client script CPU usage is anything done in onClient/Pre/Hud/Render because it is called so often. For example if you have a script which calls dxDrawLine3D 20 times, 60 times a second, if those lines are only in 1 part of the map, consider adding a [getDistanceBetweenPoints3D](/docs/getdistancebetweenpoints3d.md "wikilink") check between the local player and the general area that those lines are in and if they're no where near the player, don't draw the lines.
-   Another thing that gets called a lot and could therefore be quite consuming if not careful are events like [onClientPlayerWeaponFire](/docs/onclientplayerweaponfire.md "wikilink") and [onClientPlayerDamage](/docs/onclientplayerdamage.md "wikilink") so any scripts that use these should only be bound to the necessary elements (such as localPlayer instead of root) and run the simplest if statements for example if you wanted to handle a certain weapon being fired in a certain dimension it's better to check weapon first as that's a simple weaponID == x rather than getElementDimension(source) == y.
