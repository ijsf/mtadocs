Parameters
----------

``` lua
table detectedACList, int d3d9Size, string d3d9MD5, string d3d9SHA256
```

-   **detectedACList**: A table of [anti-cheat](/docs/anti-cheat_guide.md "wikilink") codes the player has triggered.
-   **d3d9Size**: A number representing the file size of any custom d3d9.dll the player may have installed.
-   **d3d9MD5**: A string containing the MD5 of any custom d3d9.dll the player may have installed.
-   **d3d9SHA256**: A string containing the SHA256 of any custom d3d9.dll the player may have installed.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink")

Example
-------

This example prints all information into the chatbox

``` lua

function handleOnPlayerACInfo( detectedACList, d3d9Size, d3d9MD5, d3d9SHA256 )
    outputChatBox( "ACInfo for " .. getPlayerName(source)
                .. " detectedACList:" .. table.concat(detectedACList,",")
                .. " d3d9Size:" .. d3d9Size
                .. " d3d9SHA256:" .. d3d9SHA256
                )
end
    
addEventHandler( "onPlayerACInfo", root, handleOnPlayerACInfo )

-- Ensure no one gets missed when the resource is (re)started
addEventHandler( "onResourceStart", resourceRoot,
    function()
        for _,plr in ipairs( getElementsByType("player") ) do
            resendPlayerACInfo( plr )
        end
    end
)
```

Example
-------

This example allows player serial exceptions for SD \#14 (virtual machines)

``` lua
-- List of serials which are allowed to use virtual machines
allowVM = { ["0123456789012345601234567890123456"] = true,
            ["A123637892167367281632896790123456"] = true,
            ["E123456789012347839207878392123456"] = true }

function handleOnPlayerACInfo( detectedACList, d3d9Size, d3d9MD5, d3d9SHA256 )
    for _,acCode in ipairs( detectedACList ) do
        if acCode == 14 then
            local serial = getPlayerSerial(source)
            if not allowVM[serial] then
                kickPlayer( source, "This server does not allow virtual machines." )
            end
        end
    end
end
addEventHandler( "onPlayerACInfo", root, handleOnPlayerACInfo )

-- Ensure no one gets missed when the resource is (re)started
addEventHandler( "onResourceStart", resourceRoot,
    function()
        for _,plr in ipairs( getElementsByType("player") ) do
            resendPlayerACInfo( plr )
        end
    end
)
```
