This event is triggered when an elementdata entry for an element changes. A client can perform this change on the element or it can be done using [setElementData](/setElementData.md "wikilink").

Parameters
----------

``` lua
string theName, var theOldValue
```

-   **theName**: The name of the element data entry that changed
-   **theOldValue**: The old value of this entry before it changed. The new value can be accessed using [getElementData](/getElementData.md "wikilink") ( source, theName ).

Global parameters
-----------------

-   **source**: The [source](/event_system#Event_source.md "wikilink") of this event is the [element](/element.md "wikilink") whose element data changed
-   **client**: The [client](/event_system#Event_client.md "wikilink") global variable is set to the client that called [setElementData](/setElementData.md "wikilink"), or nil if it was called on the server.
-   **sourceResource**: The [resource](/resource.md "wikilink") which changed the element data. (Only works in versions above 1.3.4-5937)

Cancelling
----------

This event cannot be cancelled using [cancelEvent](/cancelEvent.md "wikilink"). To reverse the effect, use [setElementData](/setElementData.md "wikilink") with the old value. See Example.

Example
-------

<section name="Server" class="server" show="true">
This example outputs a message to players when any of their element data values is changed.

``` lua
function outputChange(dataName,oldValue)
    if getElementType(source) == "player" then -- check if the element is a player
        local newValue = getElementData(source,dataName) -- find the new value
        outputChatBox("Your element data '"..tostring(dataName).."' has changed from '"..tostring(oldValue).."' to '"..tostring(newValue).."'",source) -- output the change for the affected player
    end
end
addEventHandler("onElementDataChange",getRootElement(),outputChange)
```

</section>
<section name="Server" class="server" show="true">
This example checks and possibly reverses an element's data change.

``` lua
function checkChange(dataName,oldValue)
    if client then
        -- The client can only set 'special_thing' on its own player
        if (dataName == "special_thing" and client ~= source) then
            outputChatBox( "Illegal setting of "..tostring(dataName).."' by '"..tostring(getPlayerName(client)) )
            setElementData( source, dataName, oldValue ) -- Set back the original value
        end
    end
end
addEventHandler("onElementDataChange",getRootElement(),checkChange)
```

</section>
