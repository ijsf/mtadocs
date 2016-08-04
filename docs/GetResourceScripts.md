<lowercasetitle></lowercasetitle>

This function show all scripts in resource.

Syntax
------

``` lua
table getResourceScripts ( resource theResource )
```

### Required Arguments

-   **theResource**: The resource where you want to get the scripts from.

### Returns

Returns *table* scripts on [resource](/resource.md "wikilink").

Code
----

<section name="Server" class="server" show="true">
``` lua
function getResourceScripts(resource)
    local scripts = {}
    local resourceName = getResourceName(resource)
    local theMeta = xmlLoadFile(":"..resourceName.."/meta.xml")
    for i, node in ipairs (xmlNodeGetChildren(theMeta)) do
        if (xmlNodeGetName(node) == "script") then
            local script = xmlNodeGetAttribute(node, "src")
            if (script) then
                table.insert(scripts, script)
            end
        end
    end
    return scripts
end
```

</section>
Example
-------

This example will compile all script on resource

<section name="Server" class="server" show="true">
``` lua
addCommandHandler("compile", 
function (source, cmd, resourceName)
    local resource = getResourceFromName(resourceName)
    if (resource) then
        for i, script in ipairs (getResourceScripts(resource)) do
            local localFile = ":"..resourceName.."/"..script
            local theScript = fileExists(localFile) and fileOpen(localFile, true)
            if (theScript) then
                local code = fileRead(theScript, fileGetSize(theScript)), fileClose(theScript)
                if not (string.byte(code) == 28) then
                    if (fetchRemote("http://luac.mtasa.com/?compile=1&debug=0&obfuscate=1", myCallback, code, true, localFile, source)) then
                        outputChatBox(localFile..": Start copy compile script...", source, 0, 255, 0)
                    else
                        outputChatBox(localFile..": Problem fetch remort", source, 255, 0, 0)
                    end
                else
                    outputChatBox(localFile..": Already compiled", source, 255, 0, 0)
                end
            else
                outputChatBox(localFile..": Does not exist or script don't opened", source, 255, 0, 0)
            end
        end
    else
        outputChatBox(resourceName..": Does not exist", source, 255, 0, 0)
    end
end)

    
function myCallback(responseData, errno, localFile, source)
    if (errno == 0) and (responseData) then
        local localFileC = localFile.."c"
        if (string.find(responseData, "ERROR")) then
            outputChatBox(localFile..": "..responseData, source, 255, 0, 0)
        else
            if (fileExists(localFileC)) then fileDelete(localFileC) end
            local theScriptC = fileCreate(localFileC)
            if (theScriptC) then
                fileWrite(theScriptC, responseData)
                fileClose(theScriptC)
                outputChatBox(localFile..": Successfully compiled", source, 0, 255, 0)
            else
                outputChatBox(localFile..": Failed to compiled", source, 255, 0, 0)
            end
        end
    else
        outputChatBox(localFile..": Failed get compiled code", source, 255, 0, 0)
    end
end
```

</section>
Credits
-------

-   **Author:** WASSIm.

See Also
--------
