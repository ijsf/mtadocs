This function outputs scripting debug messages, which can be read by enabling the debug textbox. The debug display level can then be set so that info or warning messages get filtered out.

Syntax
------

``` lua
bool outputDebugString ( string text, [ int level=3, int red=255, int green=255, int blue=255 ] )             
```

### Required Arguments

-   **text:** the text to be output to the debug box.

### Optional Arguments

-   **level:** the debug message level. Possible values are:
    -   **0:** Custom message
    -   **1:** Error message
    -   **2:** Warning message
    -   **3:** Information message (default)
-   **red:** The amount of red in the color of the text. Default value is 255.
-   **green:** The amount of green in the color of the text. Default value is 255.
-   **blue:** The amount of blue in the color of the text. Default value is 255.

**Note:** Color values are only applied when debug level is 0.

### Returns

Returns *true* if the debug message was successfully output, *false* if invalid arguments are specified.

Example
-------

<section name="Server" class="server" show="true">
This script notifies when its resource has been loaded using a debug message:

``` lua
function resourceStartNotify ( resourcename )
    -- if the started resource is this one
    if ( resourcename == getThisResource() ) then
        -- send an info debug message as a notification
        outputDebugString ( "Resource " .. getResourceName(resourcename) .. " loaded." )
    end
end
addEventHandler( "onResourceStart", getRootElement(), resourceStartNotify )
```

</section>
See Also
--------
