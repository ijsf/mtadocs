This function will trigger a named [event](/docs/event.md "wikilink") on a specific [element](/element.md "wikilink") in the [element tree](/element_tree.md "wikilink"). See [event system](/event_system.md "wikilink") for more information on how the event system works.

You can use the value returned from this function to determine if the event was cancelled by one of the event handlers. You should determine what your response (if any) to this should be based on the event's purpose. Generally, cancelling an event should prevent any further code being run that is dependent on whatever triggered that event. For example, if you have an *onFlagCapture* event, cancelling it would be expected to prevent the flag being able to be captured. Similarly, if you have *onPlayerKill* as an event you trigger, canceling it would either be expected to prevent the player being killed from dying or at least prevent the player from getting a score for it.

Syntax
------

``` lua
bool triggerEvent ( string eventName, element baseElement, [ var argument1, ... ] )    
```

### Required Arguments

-   **eventName:** The name of the event you wish to trigger
-   **baseElement:** The element you wish to trigger the event on. See [event system](/docs/event_system.md "wikilink") for information on how this works.

### Optional Arguments

-   **argument1:** The first argument that the event handler expects should be added after the *baseElement* variable.
    -   *NOTE:* This function can have more than one of these arguments specified, once for each argument the event handler is expecting.

### Returns

-   Returns **nil** if the arguments are invalid or the event could not be found.
-   Returns **true** if the event was triggered successfully, and *was not* cancelled using [cancelEvent](/docs/cancelEvent.md "wikilink").
-   Returns **false** if the event was triggered successfully, and *was* cancelled using [cancelEvent](/docs/cancelEvent.md "wikilink").

Example
-------

If you define a new custom event as follows:

``` lua
-- Add a new event called onSpecialEvent
addEvent ( "onSpecialEvent", true )
-- Define our handler function
function specialEventHandler ( text )
    outputChatBox ( text )
end
-- Add the event handler
addEventHandler ( "onSpecialEvent", root, specialEventHandler )
```

You can then trigger this event later on using:

``` lua
triggerEvent ( "onSpecialEvent", root, "test" )
```

See Also
--------

[ru:triggerEvent](/docs/ru:triggerEvent.md "wikilink")
