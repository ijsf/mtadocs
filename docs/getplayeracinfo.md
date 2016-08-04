Syntax
------

``` lua
table getPlayerACInfo( element thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") whose anti-cheat info you want to check.

### Returns

Returns a table with the following entries:

-   **DetectedAC:** A string containing a comma separated list of [anti-cheat](/docs/Anti-cheat_guide.md "wikilink") codes the player has triggered.
-   **d3d9Size:** A number representing the file size of any custom d3d9.dll the player may have installed.
-   **d3d9MD5:** A string containing the MD5 of any custom d3d9.dll the player may have installed.

Example
-------

This example checks getPlayerACInfo for changes every 3 seconds

``` lua
lastDetectedACList = {}

addEventHandler( "onResourceStart", resourceRoot,
    function()
        for _,plr in ipairs( getElementsByType("player") ) do
            lastDetectedACList[plr] = ""
        end
    end
)

addEventHandler( "onPlayerJoin", root,
    function()
        lastDetectedACList[source] = ""
    end
)

addEventHandler( "onPlayerQuit", root,
    function()
        lastDetectedACList[source] = nil
    end
)

function checkPlayersACInfo()
    for plr,lastAC in pairs( lastDetectedACList ) do
        local info = getPlayerACInfo(plr)
        if info.DetectedAC ~= lastAC then
            lastDetectedACList[plr] = info.DetectedAC
            outputServerLog( "AC-INFO: "
                .. " Player:" .. tostring(getPlayerName(plr))
                .. " DetectedAC:" .. tostring(info.DetectedAC)
                .. " d3d9MD5:" .. tostring(info.d3d9MD5)
                .. " d3d9Size:" .. tostring(info.d3d9Size)
                )
        end
    end
end
setTimer( checkPlayersACInfo, 3000, 0 )
```

Example
-------

This example allows player serial exceptions for SD \#14 (virtual machines)

``` lua
-- List of serials which are allowed to use virtual machines
allowVM = { ["0123456789012345601234567890123456"] = true,
            ["A123637892167367281632896790123456"] = true,
            ["E123456789012347839207878392123456"] = true }

function checkPlayersACInfo()
    for _,plr in ipairs( getElementsByType("player") ) do
        local ACInfo = getPlayerACInfo(plr)
        if string.find( ACInfo.DetectedAC, "14" ) then
            local serial = getPlayerSerial(plr)
            if not allowVM[serial] then
                kickPlayer( plr, "This server does not allow virtual machines." )
            end
        end
    end
end
setTimer( checkPlayersACInfo, 3000, 0 )
```

Requirements
------------

See Also
--------
