This event is triggered whenever a ped dies.

Parameters
----------

``` lua
element killer, int weapon, int bodypart, float loss
```

-   **killer**: A [player](/player.md "wikilink") [element](/element.md "wikilink") representing the killer.
-   **weapon**: An integer representing the [killer weapon](/Weapons.md "wikilink") or the [death reason](/Death_Reasons.md "wikilink").
-   **bodypart**: An integer representing the bodypart the player was damaged.

-   **loss**: A float representing the percentage of health the ped lost in the final “hit”.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [ped](/ped.md "wikilink") that died.

Example
-------

<section name="Client" class="client" show="true">
This example outputs a message every time a player kills another player.

``` lua
-- define the event handler function
function onWasted(killer, weapon, bodypart)
    if ( killer and getElementType(killer) == "player" and getElementType(source) == "player" ) then
        outputChatBox(getPlayerName(killer).." has killed ".. getPlayerName(source) ..".") -- output the kill message to the chatbox.
    end
end

-- add the event handler
addEventHandler("onClientPedWasted", getRootElement(), onWasted)
```

</section>
See Also
--------

### Client ped events

### Client event functions
