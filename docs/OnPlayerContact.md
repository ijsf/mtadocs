This event is triggered when a player stands on a different element than before.

Parameters
----------

``` lua
element previousElement, element currentElement
```

-   **previousElement**: The [element](/element.md "wikilink") player was standing on before. *nil* if none.
-   **currentElement**: The new [element](/element.md "wikilink") that the player is standing on now. *nil* if none.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") who hit an element.

Example
-------

This example outputs the element type of an element you have hit

``` lua
function outputElementType ( prev, current )
    if ( current ) then
        outputChatBox ( "You have hit an "..getElementType ( current ) )
    end
end
addEventHandler ( "onPlayerContact", getRootElement(), outputElementType )
```
