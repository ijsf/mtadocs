This event is triggered when a player issues a command.

Parameters
----------

``` lua
string command
```

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") who tried to execute a command

Cancel effect
-------------

The command will not be executed

Example
-------

This example prevents players executing more than 5 commands a second, recommended for all servers

``` lua
local commandSpam = {}

function preventCommandSpam()
    if (not commandSpam[source]) then
        commandSpam[source] = 1
        -- New person so add to table
    elseif (commandSpam[source] == 5) then
        cancelEvent()
        outputChatBox("Please refrain from command spamming!", source, 255, 0, 0)
        -- This person is command spamming!
    else
        commandSpam[source] = commandSpam[source] + 1
        -- Add one to the table
    end
end
addEventHandler("onPlayerCommand", root, preventCommandSpam)
setTimer(function() commandSpam = {} end, 1000, 0) -- Clear the table every second
```
