This event is triggered when a player or a vehicle leaves a collision shape.

Parameters
----------

``` lua
element leaveElement, bool matchingDimension
```

-   **leaveElement**: The [element](/docs/element.md "wikilink") that who exited the col shape. This can be a player or a vehicle.
-   **matchingDimension**: a boolean referring to whether the collision shape was in the same dimension as the element.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [colshape](/colshape.md "wikilink") that the element no longer is in contact with.

Example
-------

This example kills the player whenever they leave a certain collision shape:

``` lua
local jailZone = createColCircle ( 1024, 1024, 15 ) -- create a collision shape

-- call 'jailZoneLeave' whenever a player leaves the collision shape:
function jailZoneLeave ( thePlayer )
   if getElementType ( thePlayer ) == "player" then -- if the element that left was player
      killPlayer ( thePlayer ) -- kill the player
      outputChatBox ( "You are not allowed to leave the jail!", thePlayer )
   end
end
addEventHandler ( "onColShapeLeave", jailZone, jailZoneLeave )
```
