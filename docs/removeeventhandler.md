This functions removes a handler function from an [event](/docs/event.md "wikilink"), so that the function is not called anymore when the event is triggered. See [event system](/docs/event_system.md "wikilink") for more information on how the event system works.

Syntax
------

``` lua
bool removeEventHandler ( string eventName, element attachedTo, function functionVar ) 
```

### Required Arguments

-   **eventName:** The name of the [event](/docs/event.md "wikilink") you want to detach the handler function from.
-   **attachedTo:** The [element](/docs/element.md "wikilink") the handler was attached to.
-   **functionVar:** The handler function that was attached.

### Returns

Returns *true* if the event handler was removed successfully. Returns *false* if the specified event handler could not be found or invalid parameters were passed.

Example
-------

<section name="Client" class="client" show="true">
This example shows how to toggle a message on/off a screen with a command.

``` lua

function drawText() -- A function to draw the text we want
    dxDrawText(text, 10,100) -- creates a dx text 10 pixels from left, 100 from top of the screen
end
function doText(command, ...)
    if command == "starttext" then -- if player wrote /starttext
        text = table.concat({...}," ") -- then we retrieve the text
        addEventHandler("onClientRender", getRootElement(), drawText)       -- and since addEventHandler and removeEventHandler's syntax is the same, we just define the function we use later
    elseif command == "stoptext" then
        removeEventHandler("onClientRender", getRootElement(), drawText)    -- this time we use removeEventHandler
    end
end
addCommandHandler("starttext", doText) -- add two command handlers to doText function
addCommandHandler("stoptext", doText)
```

</section>
See Also
--------

[ru:removeEventHandler](/docs/ru:removeeventhandler.md "wikilink")
