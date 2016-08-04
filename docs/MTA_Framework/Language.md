<pageclass class="server"></pageclass> The language system is a small system. But really it helps you a lot!

For example. Someone just found a pot of gold, you can simple do ([Chatbox functions](/MTA_Framework/Chatbox.md "wikilink")):

``` lua
local Event = eventLoader:loadServerEvents();

Event.onPickupHit(function(player)
    local ch = ChatBox:init(player);
    ch:say("L_PLAYER_HIT_GOLD", getPlayerName(player));
end);
```

That is so easy to use language variables. In normal mta you will do this:

``` lua
function pickupHit(player)
    outputChatBox("You just hit a pot of gold. Congratulations " .. getPlayerName(player) .. ".", player);
end

addEventHandler("onPickupHit", getRootElement(), pickupHit);
```

So the language system is bigger then only outputing a variable into the chatbox. You need to create the language files and variables.

Language loader
---------------

Language parser
---------------

Create an language
------------------
