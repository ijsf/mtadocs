This event is triggered when the model of an [element](/docs/element.md "wikilink") is changed using [setElementModel](/setElementModel.md "wikilink").

Parameters
----------

``` lua
int oldModel
```

-   **oldModel:** The model of the element beforehand.

Source
------

The source of this event is the element that changed its model

Cancel Effect
-------------

This event doesn't support [cancellation](/docs/event_system#canceling.md "wikilink"). Use setElementModel with the old value to reverse.

Example
-------

This example sends a message to players when their model changes telling them what the model ID is and was.

``` lua
function informPlayerOnModelChange(oldModel)
    if ( getElementType(source) == "player" ) then -- Make sure the element is a player
        outputChatBox("Model ID changing from: "..oldModel.." to: "..getElementModel(source), source, 0, 255, 0) -- Message for player
    end
end
addEventHandler("onElementModelChange", root, informPlayerOnModelChange) -- Bind the event to every element
```

See Also
--------

### Element events

### Event functions
