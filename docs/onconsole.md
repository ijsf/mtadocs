This event is triggered when a player types a message into his console. It is also triggered when entering '/' commands via the chatbox.

Parameters
----------

``` lua
string theMessage
```

-   **theMessage**: a string representing the message typed into the console.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that entered the message in the console. This can be a player or the server console.

Example
-------

This example adds the *yo* command into the script. For example, if a player called Bob types “yo likes pie” in console, it will display "\* Bob likes pie" in the chatbox.

  
**NOTE:** this script is for example purposes only. This can be done in a more efficient way with [addCommandHandler](/docs/addcommandhandler.md "wikilink").

``` lua
function input_Console ( text ) --when a player types in the console
    -- if it's an ingame player,
    if ( getElementType ( source ) == "player" ) then
        --split the command by spaces (ASCII 32) and get the first piece of text
        local command = gettok ( text, 1, 32 )
        --if the first piece of text was "yo",
        if ( command == "yo" ) then
            --get the player's name
            local playerName = getPlayerName ( source )
            -- get the action text by substracting the first three characters ("yo ")
            local actionText = string.sub ( text, 3 )
            -- announce the yo command into the chatbox
            outputChatBox ( "* " .. playerName .. " " .. actionText, getRootElement(), 255, 255, 0 )
        end
    end
end
addEventHandler ( "onConsole", getRootElement(), input_Console ) -- add an event handler for onConsole
```

[ru:onConsole](/docs/ru:onconsole.md "wikilink")
