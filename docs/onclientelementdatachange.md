This event is triggered whenever an element's *[data](/docs/element_data.md "wikilink")* is changed.

Parameters
----------

``` lua
string dataName, string oldValue
```

-   **dataName**: A string representing the element data that was changed
-   **oldValue**: A string representing the value before changed element data

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [element](/docs/element.md "wikilink") that had its element data changed

Example
-------

This example tells the client whenever a player's “score” element data is changed.

``` lua
addEventHandler ( "onClientElementDataChange", getRootElement(),
function ( dataName )
    if getElementType ( source ) == "player" and dataName == "score" then
        outputChatBox ( getPlayerName(source).."'s new score is "..getElementData (source, "score").."!" )
    end
end )
```

[pl:onClientElementDataChange](/docs/pl-onclientelementdatachange.md "wikilink")

See Also
--------

### Client element events

### Client event functions
