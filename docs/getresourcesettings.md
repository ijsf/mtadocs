<lowercasetitle></lowercasetitle>

This function returns a table of the resource settings.

Syntax
------

``` lua
table getResourceSettings( resource theResource )
```

### Required Arguments

-   **theResource**: The resource where you want to get the settings from.

### Optional Arguments

Code
----

<section name="Serverside Script" class="server" show="true">
``` lua
function getResourceSettings ( resource )
    if ( not resource ) then
        return false
    end

    local settingsTable = { }
    local name          = getResourceName ( resource )
    local meta          = xmlLoadFile     ( ":".. name .."/meta.xml" )
    if ( not meta ) then
        return false
    end

    local settings      = xmlFindChild    ( meta, "settings", 0 )
    if ( settings ) then
        for _, setting in ipairs ( xmlNodeGetChildren ( settings ) ) do
            local oldName      = xmlNodeGetAttribute ( setting, "name" )
            local temp         = string.gsub ( oldName, '[%*%#%@](.*)','%1' )
            table.insert (
                settingsTable,
                    {
                        string.gsub ( temp, name ..'%.(.*)','%1' ),
                        xmlNodeGetAttribute ( setting, "value" ),
                        xmlNodeGetAttribute ( setting, "friendlyname" ),
                        xmlNodeGetAttribute ( setting, "accept" ),
                        xmlNodeGetAttribute ( setting, "desc" ),
                        xmlNodeGetAttribute ( setting, "group" )
                    }
                )
        end
    end

    xmlUnloadFile ( meta )
    return settingsTable
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example get's the settings count from a resource.

``` lua
function getResourceSettings ( resource )
    if ( not resource ) then
        return false
    end

    local settingsTable = { }
    local name          = getResourceName ( resource )
    local meta          = xmlLoadFile     ( ":".. name .."/meta.xml" )
    if ( not meta ) then
        return false
    end

    local settings      = xmlFindChild    ( meta, "settings", 0 )
    if ( settings ) then
        for _, setting in ipairs ( xmlNodeGetChildren ( settings ) ) do
            local oldName      = xmlNodeGetAttribute ( setting, "name" )
            local temp         = string.gsub ( oldName, '[%*%#%@](.*)','%1' )
            table.insert (
                settingsTable,
                    {
                        string.gsub ( temp, name ..'%.(.*)','%1' ),
                        xmlNodeGetAttribute ( setting, "value" ),
                        xmlNodeGetAttribute ( setting, "friendlyname" ),
                        xmlNodeGetAttribute ( setting, "accept" ),
                        xmlNodeGetAttribute ( setting, "desc" ),
                        xmlNodeGetAttribute ( setting, "group" )
                    }
                )
        end
    end

    xmlUnloadFile ( meta )
    return settingsTable
end

-- define the command handler function
function countSettings ( thePlayer, commandName, resourceName )
    local settings = getResourceSettings ( getResourceFromName ( resourceName ) )
    if ( settings ) then
        outputChatBox ( "This resource has: ".. #settings .." settings.", thePlayer ) -- output the count to the chatbox.
    end
end
-- add the command handler
addCommandHandler ( "settings", countSettings )
```

</section>
Author: Castillo

See Also
--------
