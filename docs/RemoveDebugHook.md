Syntax
------

``` lua
bool removeDebugHook( string hookType, function callbackFunction )
```

### Required Arguments

-   **hookType:** The type of hook to remove. This can be:
    -   preEvent
    -   postEvent
    -   preFunction
    -   postFunction
-   **callbackFunction :** The callback function to remove

### Returns

Returns *true* if the hook was successfully removed, or *false* otherwise.

Example
-------

This example adds a hook, then removes it:

``` lua
function onPreEvent( sourceResource, eventName, eventSource, eventClient, luaFilename, luaLineNumber, ... )
end
addDebugHook( "preEvent", onPreEvent )
removeDebugHook( "preEvent", onPreEvent )
```

Changelog
---------

Requirements
------------

See Also
--------
