This event is triggered when a player is damaged, in any way.

-   This event is not triggered when attacked by a team member if friendly fire is enabled.
-   Canceling this event has no effect. Cancel the client-side event [onClientPlayerDamage](/docs/onclientplayerdamage.md "wikilink") instead.
-   onPlayerDamage doesn't trigger if the damage kills the player, [onPlayerWasted](/docs/onplayerwasted.md "wikilink") is called instead.

Parameters
----------

``` lua
player attacker, int attackerweapon, int bodypart, float loss
```

-   **attacker**: A player element representing the player who was the attacker. If there was no attacker this returns false.
-   **attackerweapon**: An integer representing the weapon the attacker used to kill the player
-   **bodypart**: An integer representing the bodypart ID the player was hit on when he got damaged.

-   **loss**: A float representing the percentage of health the player lost.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/docs/player.md "wikilink") who was damaged.

Example
-------

This example causes an instant kill when a player is shot in the head, and announces it in the chatbox.

``` lua
--add an event handler for the onPlayerDamage event
function playerDamage_text ( attacker, weapon, bodypart, loss ) --when a player is damaged
    if ( bodypart == 9 ) then -- if the body part is 9, i.e. the head
            outputChatBox ( "Headshot!", getRootElement (), 255, 170, 0 ) --output "Headshot" into the chatbox
        killPed ( source, attacker, weapon, bodypart ) -- and kill the player
    end
end
addEventHandler ( "onPlayerDamage", getRootElement (), playerDamage_text )
```

Issues
------
