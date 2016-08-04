This event is triggered whenever a player, including those remote, dies.

Parameters
----------

``` lua
element killer, int weapon, int bodypart
```

-   **killer**: A [player](/docs/player.md "wikilink") [element](/docs/element.md "wikilink") representing the killer.
-   **weapon**: An integer representing the [killer weapon](/docs/weapons.md "wikilink") or the [death reason](/docs/death_reasons.md "wikilink").
-   **bodypart**: An integer representing the bodypart the player was damaged.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/docs/player.md "wikilink") that died.

Example
-------

This example outputs a mocking message when the local player dies.

``` lua
messages = { 
"Better luck next time",
"Don't think you're so cool now, do you?",
"Nice one, pal",
"Your opinion is void" 
}

function wastedMessage ( killer, weapon, bodypart )
    local randomID = math.random ( 1, #messages ) --get a random ID from the table
    local randomMessage = messages[randomID] --use that to retrieve a message
    outputChatBox ( randomMessage, 255, 0, 0 ) --output the message
end
addEventHandler ( "onClientPlayerWasted", getLocalPlayer(), wastedMessage ) --add an event for the local player only
```

See Also
--------

### Client player events

### Client event functions
