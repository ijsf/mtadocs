This event is fired before an object breaks.

Parameters
----------

``` lua
element attacker
```

-   **attacker:** the vehicle/ped/player who is breaking the object

Source
------

The source of this event is the object which will break.

Cancel effect
-------------

If this event is [canceled](/docs/Event_system#Canceling.md "wikilink"), the object will not break.

Example
-------

<section class="client" name="Client" show="true">
This example prevents objects from beeing broken in interiors.

``` lua
addEventHandler("onClientObjectBreak", root,
    function()
        if getElementInterior(source) ~= 0 then
            cancelEvent()
        end
    end
)
```

</section>
Requirements
------------

See Also
--------

### Client object events

### Client event functions
