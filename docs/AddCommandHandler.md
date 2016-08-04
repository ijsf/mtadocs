This function will attach a scripting function (handler) to a console command, so that whenever a player or administrator uses the command the function is called. **Note:** You cannot use “list” or “test” as command name.

Multiple command handlers can be attached to a single command, and they will be called in the order that the handlers were attached. Equally, multiple commands can be handled by a single function, and the *commandName* parameter used to decide the course of action.

For users, a command is in the format:

*commandName* *argument1* *argument2*

This can be triggered from the player's console or directly from the chat box by prefixing the message with a forward slash (*/*). For server side handlers, the server admin is also able to trigger these directly from the server's console in the same way as they are triggered from a player's console.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool addCommandHandler ( string commandName, function handlerFunction, [bool restricted = false, bool caseSensitive = true] )
```

### Required Arguments

-   **commandName:** This is the name of the command you wish to attach a handler to. This is what must be typed into the console to trigger the function.
-   **handlerFunction:** This is the function that you want the command to trigger, which has to be defined before you add the handler. This function can take two parameters, playerSource and commandName, followed by as many parameters you expect after your command (see below). These are all optional.

### Optional Arguments

-   **restricted:** Specify whether or not this command should be restricted by default. Use this on commands that should be inaccessible to everyone as default except special users specified in the ACL (Access Control List). This is to make sure admin commands such as ie. 'punish' won't be available to everyone if a server administrator forgets masking it in ACL. Make sure to add the command to your ACL under the proper group for it to be usefull (i.e <right name="command.killEveryone" access="true"></right>). This argument defaults to false if nothing is specified.

</section>
<section name="Client" class="client" show="true">
``` lua
bool addCommandHandler ( string commandName, function handlerFunction, [bool caseSensitive = true] )
```

### Required Arguments

-   **commandName:** This is the name of the command you wish to attach a handler to. This is what must be typed into the console to trigger the function.
-   **handlerFunction:** This is the function that you want the command to trigger, which has to be defined before you add the handler. This function can take two parameters, playerSource and commandName, followed by as many parameters you expect after your command (see below). These are all optional.

### Optional Arguments

</section>
#### Handler function parameters

These are the parameters for the handler function that is called when the command is used.

<section name="Server" class="server" show="true">
``` lua
 
```

-   **playerSource:** The player who triggered the command. If not triggered by a player (e.g. by admin), this will be *false*.
-   **commandName:** The name of the command triggered. This is useful if multiple commands go through one function.
-   **arg1, arg2, ...:** Each word after command name in the original command is passed here in a seperate variable. If there is no value for an argument, its variable will contain [nil](/nil.md "wikilink"). You can deal with a variable number of arguments using the vararg expression, as shown in **Server Example 2** below.

</section>
<section name="Client" class="client" show="true">
``` lua
 
```

-   **commandName:** The name of the command triggered. This is useful if multiple commands go through one function.
-   **arg1, arg2, ...:** Each word after command name in the original command is passed here in a seperate variable. If there is no value for an argument, its variable will contain [nil](/nil.md "wikilink"). You can deal with a variable number of arguments using the vararg expression, as shown in **Server Example 2** below.

</section>
### Returns

Returns *true* if the command handler was added successfully, *false* otherwise.

Examples
--------

<section name="Server" class="server" show="true">
**Example 1:** This example defines a command handler for the command *createmarker*. This will create a red marker at the position of the player player who uses it.

``` lua
-- Define our function that will handle this command
function consoleCreateMarker ( playerSource )
    -- If a player triggered it (rather than the admin) then
    if ( playerSource ) then
        -- Get that player's position
        local x, y, z = getElementPosition ( playerSource )
        -- Create a size 2, red checkpoint marker at their position
        createMarker ( x, y, z, "checkpoint", 2, 255, 0, 0, 255 )
        -- Output it in his chat box
        outputChatBox ( "You got a red marker", playerSource )
    end
end
-- Attach the 'consoleCreateMarker' function to the "createmarker" command
addCommandHandler ( "createmarker", consoleCreateMarker )
```

</section>
<section name="Server" class="server" show="hide">
**Example 2:** This example makes use of Lua's vararg expression to implement a *check\_parameters* command to count the number of parameters passed, merge them all into a single string and output it. This is also shows you how you can use table.concat to merge all the passed arguments. This is particularly useful when you want to read in a sentence of text passed from the user.

``` lua
-- Define our function that will handle this command (which can accept a variable number of arguments after commandName)
function consoleCheckParameters ( playerSource, commandName, ... )
    -- If a player, not an admin, triggered it,
    if playerSource then
        local arg = {...}
        -- Get the number of arguments in the arg table (arg table is the same as: {...})
        local parameterCount = #arg
        -- Output it to the player's chatbox
        outputChatBox ( "Number of parameters: " .. parameterCount, playerSource )
        -- Join them together in a single comma-separated string
        local stringWithAllParameters = table.concat( arg, ", " )
        -- Output this parameter list to the player's chatbox
        outputChatBox ( "Parameters passed: " .. stringWithAllParameters, playerSource )
    end
end
-- Attach the 'consoleCheckParameters' function to the "check_parameters" command
addCommandHandler ( "check_parameters", consoleCheckParameters )
```

</section>
<section name="Server" class="server" show="hide">
**Example 3:** This example shows using a single function to handle multiple command handlers. This isn't advised for general usage, as it makes code harder to understand, but where multiple command handlers share some logic, it can be a useful way of reducing duplicated code. Generally, it would be preferable to put this shared logic in a separate function instead, as this gives you more control over the flow.

``` lua
-- make the function
function moneyCmd(player, cmd, amount)
    if getElementData(player, "canUseMoneyFunctions") then -- the shared logic
        if cmd == "givemoney" then
            amount  = tonumber(amount)
            if amount then
                givePlayerMoney(player, amount)
            else
                outputChatBox("[usage] /givemoney [amount]", player)
            end
        else if cmd == "takemoney" then
            amount = tonumber(amount)
            if amount then
                takePlayerMoney(player, amount)
            else
                outputChatBox("[usage] /takemoney [amount]", player)
            end
        end
    else
        outputChatBox("You aren't able to use this command", player)
    end
end
 
addCommandHandler("givemoney", moneyCmd);
addCommandHandler("takemoney", moneyCmd);
```

</section>
<section name="Client" class="client" show="false">
**Example 1:** This example warps the local player to a random nearby location (useful for when a player gets stuck somewhere).

``` lua
function escapeMe ()
    local x, y, z = getElementPosition ( localPlayer ) --Get player's position
    setElementPosition ( localPlayer, x+(math.random(-10,10)), y+(math.random(-10,10)), z+(math.random(1,15)) ) --Move a player randomly to a nearby location. X is current x + a number between -10, 10 and so on.
end    
addCommandHandler ( "escape", escapeMe ) --When player types "/escape" in chatbox or "escape" in console
```

</section>
See Also
--------
