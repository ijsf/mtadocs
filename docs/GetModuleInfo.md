This function returns information about the specified [module](/Modules.md "wikilink").

Syntax
------

``` lua
table getModuleInfo ( string moduleName )
```

### Required Arguments

-   **moduleName:** A string containing the module you wish to get information of e.g. “hashing.dll”

### Returns

Returns a [table](/table.md "wikilink") containing information about module. These keys are present in the table:

-   **version**: Module version in format X.XX
-   **name**: Module name
-   **author**: Module author

If invalid name for module is passed, it will return *false*.

Example
-------

This example adds a command *checkmodules* with which you can view information about currently loaded modules.

``` lua
function printModuleInfo ( thePlayer )
    local modules = getLoadedModules()
    if #modules == 0 then
        return outputConsole ( "There are no modules loaded!", thePlayer ) -- Return as no module is loaded, the for has nothing todo
    end

    for k, v in ipairs ( modules ) do
        local moduleInfo = getModuleInfo ( v )
        outputConsole ( moduleInfo.name .. "(" .. v .. ") v" .. moduleInfo.version .. ", author: " .. moduleInfo.author, thePlayer )
    end
end
addCommandHandler ( "checkmodules", printModuleInfo )
```

See Also
--------

[ru:getModuleInfo](/ru:getModuleInfo.md "wikilink")
