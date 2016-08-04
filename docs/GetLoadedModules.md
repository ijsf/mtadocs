This function returns all the currently loaded [modules](/modules.md "wikilink") of the server.

Syntax
------

``` lua
table getLoadedModules ()
```

### Returns

Returns a table of all the currently loaded [modules](/modules.md "wikilink"). If no modules are loaded, the table will be empty.

Example
-------

Adds a command that lists all loaded modules in the server log.

``` lua
function checkModules()
    local modules = getLoadedModules()
    
    if #modules == 0 then
        return outputServerLog("No modules are loaded!")
    end
    
    for k,v in ipairs(modules) do
            outputServerLog( v )
    end
        
    outputServerLog("Loaded " .. #modules .. " modules in total.")
end
addCommandHandler("modules", checkModules)
```

See Also
--------

[ru:getLoadedModules](/ru:getLoadedModules.md "wikilink")
