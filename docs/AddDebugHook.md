Syntax
------

``` lua
bool addDebugHook( string hookType, function callbackFunction[, table nameList ] )
```

### Required Arguments

-   **hookType:** The type of hook to add. This can be:
    -   preEvent
    -   postEvent
    -   preFunction
    -   postFunction
-   **callbackFunction :** The function to call

### Optional Arguments

-   **nameList:** Table of strings for restricting which functions and events the hook will be triggered on

### Returns

Returns *true* if the hook was successfully added, or *false* otherwise.

Callback parameters
-------------------

``` lua
string preFunction( resource sourceResource, string functionName, bool isAllowedByACL, string luaFilename, int luaLineNumber, functionArguments )
       postFunction( resource sourceResource, string functionName, bool isAllowedByACL, string luaFilename, int luaLineNumber, functionArguments )
string preEvent( resource sourceResource, string eventName, element eventSource, element eventClient, string luaFilename, int luaLineNumber, eventArguments )
       postEvent( resource sourceResource, string eventName, element eventSource, element eventClient, string luaFilename, int luaLineNumber, eventArguments )
```

Example
-------

This example will dump info about all triggered events:

``` lua
function onPreEvent( sourceResource, eventName, eventSource, eventClient, luaFilename, luaLineNumber, ... )
    local args = { ... }
    local srctype = eventSource and getElementType(eventSource)
    local resname = sourceResource and getResourceName(sourceResource)
    local plrname = eventClient and getPlayerName(eventClient)
    outputDebugString( "preEvent"
        .. " " .. tostring(resname)
        .. " " .. tostring(eventName)
        .. " source:" .. tostring(srctype)
        .. " player:" .. tostring(plrname)
        .. " file:" .. tostring(luaFilename)
        .. "(" .. tostring(luaLineNumber) .. ")"
        .. " numArgs:" .. tostring(#args)
        .. " arg1:" .. tostring(args[1])
        )
end
addDebugHook( "preEvent", onPreEvent )
```

This example will dump info about all called MTA functions:

``` lua
function onPreFunction( sourceResource, functionName, isAllowedByACL, luaFilename, luaLineNumber, ... )
    local args = { ... }
    local resname = sourceResource and getResourceName(sourceResource)
    outputDebugString( "preFunction"
        .. " " .. tostring(resname)
        .. " " .. tostring(functionName)
        .. " allowed:" .. tostring(isAllowedByACL)
        .. " file:" .. tostring(luaFilename)
        .. "(" .. tostring(luaLineNumber) .. ")"
        .. " numArgs:" .. tostring(#args)
        .. " arg1:" .. tostring(args[1])
        )
end
addDebugHook( "preFunction", onPreFunction)
```

This example adds a hook which will only be triggered for the named functions

``` lua
addDebugHook( "preFunction", onPreFunction, {"setElementPosition","loadstring"} )
```

Changelog
---------

Requirements
------------

See Also
--------
