This event is triggered when client-side debug messages (for instance errors or warnings) would appear in the debug window. This event doesn't require the debug window to be enabled to trigger, however.

Parameters
----------

``` lua
string message, int level, string file, int line
```

-   **message**: The message which was outputted in the server console, without details like file, line etc
-   **level**: The type of debug message which was outputted
    -   **0:** “Custom” message
    -   **1:** Error message
    -   **2:** Warning message
    -   **3:** Information message
-   **file**: The file from which the debug message was outputted
    -   **Note:** May return [nil](/docs/nil.md "wikilink") when the source could not be found
-   **line**: The line in file **file** where the debug message was outputted
    -   **Note:** May return [nil](/docs/nil.md "wikilink") when the source could not be found

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [root element](/root_element.md "wikilink").

Examples
--------

This (easy) example outputs the debug message in the console, so you don't need to open debugscript 3 :D

``` lua
addEventHandler ("onClientDebugMessage",getRootElement(),
function(message,level,file,line)
  outputConsole (message,getLocalPlayer())
end)
```

This example tells players that they missed a debug message, if they don't have debugscript enabled.

``` lua
function newDebug() -- Since we don't need any of the parameters, we can optimize the code and exclude them
    if not isDebugViewActive() then -- If their debug view is not active
        outputChatBox("* You just missed a debug message. Use the \'/debugscript\' command to view it.",255,0,0) -- Output to them that they missed a debug message
    end
end
addEventHandler("onClientDebugMessage",root,newDebug) -- When we get a new client debug message, call the newDebug function
```

See Also
--------

### Other client events

### Client event functions
