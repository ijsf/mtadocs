With this function, you can check if a ped has a head or not.

Syntax
------

``` lua
bool isPedHeadless  ( ped thePed )
```

### Required Arguments

-   **thePed**: The [ped](/docs/ped.md "wikilink") to check.

### Returns

Returns *true* if the ped is headless, *false* otherwise.

Example
-------

<section class="client" name="Client" show="true">
Add a command to check whether the player is a zombie or not

``` lua
function checkZombie(commandName)
   local player = getLocalPlayer()
   -- check whether the player is headless (a zombie)
   local message = isPedHeadless(player) and "Yes, you are a zombie!" or "No, you aren't a zombie yet!"
   outputChatBox(message)
end

addCommandHandler("zombie", checkZombie)
```

</section>
<section class="server" name="Server" show="true">
Add a command to check whether a player is a zombie or not

``` lua
function checkZombie(playerSource, commandName, playerTargetNick)
   local playerTarget = getPlayerFromName(playerTargetNick)
   if (not playerTarget) then return outputChatBox("Player not online!", playerSource, 255, 0, 0) end

   -- check whether the playerTarget is headless (a zombie)
   local message = isPedHeadless(playerTarget) and "This Player is a zombie!" or "This player is not a zombie!"
   outputChatBox(message, playerSource)
end

addCommandHandler("zombie", checkZombie)
```

</section>
See Also
--------
