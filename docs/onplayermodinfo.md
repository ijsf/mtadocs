This event is triggered when a player has modified certain files.

Parameters
----------

``` lua
string filename, table itemlist
```

-   **filename**: An string with the filename of the modified file
-   **itemlist**: A table with the details of each modification within the file.
    -   Possible keys for each sub-table are:
    -   **id**: GTA model or texture id
    -   **name**: GTA name

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink")

Example
-------

This example prints all information into the chatbox

``` lua

function handleOnPlayerModInfo ( filename, modList )
    -- Print player name and file name
    outputChatBox( getPlayerName(source) .. " " .. filename )

    -- Print details on each modification
    for idx,item in ipairs(modList) do
        outputChatBox( idx .. ") id:" .. item.id .. " name:" .. item.name )
        if item.sizeX then
            outputChatBox( "size:" .. item.sizeX .. "," .. item.sizeY .. "," .. item.sizeZ )
            outputChatBox( "originalSize:" .. item.originalSizeX .. "," .. item.originalSizeY .. "," .. item.originalSizeZ )
        end
        if item.length then
            outputChatBox( "length:" .. item.length .. " md5:" .. item.md5 )
        end
    end
end
    
addEventHandler ( "onPlayerModInfo", getRootElement(), handleOnPlayerModInfo )

-- Ensure no one gets missed when the resource is (re)started
addEventHandler( "onResourceStart", resourceRoot,
    function()
        for _,plr in ipairs( getElementsByType("player") ) do
            resendPlayerModInfo( plr )
        end
    end
)
```

This example checks modified files against a list and prints a warning in the chatbox

``` lua

checkModels = { "m4.dff", "ak47.dff" }

function handleOnPlayerModInfo ( filename, modList )
    for _,item in ipairs(modList) do            -- Check each modified item
        for _,checkName in ipairs(checkModels) do
            if item.name == checkName then      -- See if modified item is in our check list
                outputChatBox ( "Not allowed to used modified weapons. Please restore " .. filename )
            end
        end
    end
end
    
addEventHandler ( "onPlayerModInfo", getRootElement(), handleOnPlayerModInfo )

-- Ensure no one gets missed when the resource is (re)started
addEventHandler( "onResourceStart", resourceRoot,
    function()
        for _,plr in ipairs( getElementsByType("player") ) do
            resendPlayerModInfo( plr )
        end
    end
)
```
