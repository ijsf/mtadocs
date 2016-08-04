<lowercasetitle></lowercasetitle>

This function loads a resource script

Syntax
------

``` lua
boolean loadScript( string file, resource theResource )
```

### Required Arguments

-   **fileName**: A string referencing the name of the script to load.
-   **theResource**: the resource we are load script from.

### Returns

Returns *true* if file script has been loaded, *false* otherwise.

Code
----

``` lua

function loadScript(file, resource)
    local file = fileOpen(file)
    if (file) then
        local resourceName = getResourceName(resource)
        local script = resourceName and ":"..resourceName.."/"..file.."" or ""
        local content = fileRead(script, fileGetSize(script))
        local loaded = loadstring(content)
        fileClose(file)
        if (loaded) then
            return true
        end
    end
    return false
end
```

Example
-------

This example load script from resource by command

``` lua

addCommandHandler("loadscript",
function (thePlayer, cmd, resource, script)
    local theResource = getResourceFromName(resource)
    if (theResource) then
        if (loadScript(script, theResource)) then
            outputChatBox("Script "..script.." has been loaded from resource "..resource, thePlayer, 0, 255, 0)
        else
            outputChatBox("The resource "..resource.." not exist", thePlayer, 255, 0, 0)
        end
    else
        outputChatBox("use /loadscript (resourcename) (scriptname)", thePlayer, 255, 0, 0)
    end
end)
 
```

Credits
-------

-   **Author:**: WASSIm.

See Also
--------
