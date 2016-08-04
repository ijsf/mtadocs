<lowercasetitle/>

This code refreshes your resource if any part of the code or some resource file has changed, it works just like “refreshResources ()” but adapted for one particular resource

Syntax
------

``` lua
refreshResource()
```

Return
------

Returns **false** if none has changed

code
----

``` lua
local Bytes = 0
addEventHandler("onResourceStart", resourceRoot,
    function()
    local meta = xmlLoadFile(":"..getResourceName(getThisResource()).."/meta.xml")
        if meta then
            for k,v in ipairs(xmlNodeGetChildren(meta)) do
                if fileExists(xmlNodeGetAttribute(v, "src")) then
                local file = fileOpen(xmlNodeGetAttribute(v, "src"))
                local _ = fileGetSize(file)
                Bytes = Bytes + _
                fileClose(file)
                end
            end
        end
    end
)
--USEFUL FUNCTION
function refreshResource ()
local newBytes = 0
local meta = xmlLoadFile(":"..getResourceName(getThisResource()).."/meta.xml")
    if meta then
        for k,v in ipairs(xmlNodeGetChildren(meta)) do
            if fileExists(xmlNodeGetAttribute(v, "src")) then
            local file = fileOpen(xmlNodeGetAttribute(v, "src"))
            local _ = fileGetSize(file)
            newBytes = newBytes + _
            fileClose(file)
            end
        end
        if newBytes ~= Bytes then
        print(getResourceName(getThisResource()).." has changed.. reloading...")
        restartResource(getThisResource())
        else
        return false
        end
    end
end
```

Example
-------

<section name="Example" class="server" show="true">
TODO.

``` lua
TODO
```

</section>
See Also
--------
