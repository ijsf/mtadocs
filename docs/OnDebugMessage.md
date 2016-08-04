This event is triggered when debug messages (for instance errors or warnings) appear in the server console.

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
    -   **Note:** May return [nil](/nil.md "wikilink") when the source could not be found
-   **line**: The line in file **file** where the debug message was outputted
    -   **Note:** May return [nil](/nil.md "wikilink") when the source could not be found

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [root element](/root_element.md "wikilink").

Example
-------

This example outputs all debug messages to the chat box with the same colouring.

``` lua
addEventHandler("onDebugMessage", getRootElement(), 

function(message, level, file, line)

if level == 1 then
    outputChatBox("ERROR: " .. file .. ":" .. tostring(line) .. ", " .. message, getRootElement(), 255,0,0)
elseif level == 2 then
    outputChatBox("WARNING: " .. file .. ":" .. tostring(line) .. ", " .. message, getRootElement(), 255,165,0)
else
    outputChatBox("INFO: " .. file .. ":" .. tostring(line) .. ", " .. message, getRootElement(), 0,0,255)
end


end)
```
