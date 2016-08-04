This event is triggered when a player targets an element with his crosshair while aiming, or simply facing it while standing close. It's triggered again when the player no longer targets anything.

Parameters
----------

``` lua
element targettedElement
```

-   **targettedElement**: The element the player is targetting. *false* if no element is being targetted anymore.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/docs/player.md "wikilink") that is targetting the element.

Example
-------

<section name="Server" class="server" show="true">
This example destroys a haystack when a player targets it

``` lua
function onPlayerTarget ( targetElem )
    -- if the targeted object is a haystack (an object with model ID 3374) remove it from the game
    if getElementType ( targetElem ) == "object" and getElementModel ( targetElem ) == 3374 then
        destroyElement ( targetElem )
    end
end
addEventHandler ( "onPlayerTarget", getRootElement(), onPlayerTarget )    -- add above function as handler for targeting event
```

</section>
