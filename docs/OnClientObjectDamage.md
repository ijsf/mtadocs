This event is fired before an object gets damaged.

Parameters
----------

``` lua
float loss, element attacker
```

-   **loss:** the health loss caused by the damage. This parameter contains the theoretical loss, which could be less than 0, if you substract it of the current health. If you want to get the real loss, you have to substract the new health of the old health (use a timer for this).
-   **attacker:** the vehicle/ped/player who is damaging the object

Source
------

The source of this event is the object which was damaged

Cancel effect
-------------

If this event is [canceled](/Event_system#Canceling.md "wikilink"), the object will not be damaged.

Example
-------

This example outputs the theoretical and real loss.

``` lua
function outputLoss(loss)
    local oldHealth = getElementHealth(source)
    setTimer(function()
        local newHealth = getElementHealth(source)
        outputChatBox("Real loss: "..(newHealth-oldHealth))
        outputChatBox("Theoretical loss: "..loss)
    end,100,1)
end
addEventHandler("onClientObjectDamage", root, outputLoss)
```

Requirements
------------

See Also
--------

### Client object events

### Client event functions
