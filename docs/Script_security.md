Detecting and dealing with the effects of rogue clients
-------------------------------------------------------

To ensure minimum damage when a player with a hacked client connects to your server:

-   When making scripts, remember to never trust data coming from a client.
-   When reviewing scripts for possible security holes. Look at any data coming from the client that is being trusted.

How to never trust data coming from a client
--------------------------------------------

A hacked client could send anything, so all client data received by server scripts should be validated before use. Most data is received via client calls to [setElementData](/setElementData.md "wikilink") or [triggerServerEvent](/triggerServerEvent.md "wikilink").

Validating client setElementData
--------------------------------

-   All parameters including 'source' can be faked and should not be trusted.
-   Global variable 'client' can be trusted.

------------------------------------------------------------------------

<section name="Server" class="server" show="true">
Example validation of element data changes

``` lua
addEventHandler("onElementDataChange", root,
    function(dataName, oldValue)
        -- Check data is coming from a client
        if client then

            -- Validate 'special_thing'
            if dataName == "special_thing" then
                -- 'special_thing' can only be set by a client on its own player
                if client ~= source then
                    -- Illegal activity here, so log and revert the change
                    reportAndRevertDataChange( dataName, oldValue, source, client )
                end
            end

            -- Validate 'flag_waving'
            if dataName == "flag_waving" then
                -- 'flag_waving' can only be set by a client on its own vehicle
                local vehicle = getPedOccupiedVehicle(client)
                if vehicle ~= source then
                    -- Illegal activity here, so log and revert the change
                    reportAndRevertDataChange( dataName, oldValue, source, client )
                end
            end

        end
    end
)

-- Helper function to log and revert changes
function reportAndRevertDataChange( dataName, oldValue, source, client )
    -- Report
    outputConsole( "Possible rouge client!"
            .. " client:" .. tostring(getPlayerName(client))
            .. " dataName:" .. tostring(dataName)
            .. " oldValue:" .. tostring(oldValue)
            .. " newValue:" .. tostring(getElementData(source,dataName))
            .. " source:" .. tostring(source)
            )
    -- Revert (Note this will cause an onElementDataChange event, but 'client' will be nil)
    setElementData( source, dataName, oldValue )               
end
```

</section>
Validating client triggerServerEvent
------------------------------------

-   All parameters including 'source' can be faked and should not be trusted.
-   Global variable 'client' can be trusted.

------------------------------------------------------------------------

<section name="Server" class="server" show="true">
Example validation of event parameters

``` lua
addEvent("onRaiseTheRoof", true)
addEventHandler("onRaiseTheRoof", resourceRoot,
    function(arg1, arg2)
        -- Check data is coming from a client
        if client then

            -- The source for this event is always 'resourceRoot'
            if source ~= resourceRoot then
                reportNaughtyness( eventName, client, "source" )
                return
            end

            -- arg1 should be the player
            if arg1 ~= client then
                reportNaughtyness( eventName, client, "arg1" )
                return
            end

            -- arg2 should be between 1 and 100
            if arg2 < 1 or arg2 >100 then
                reportNaughtyness( eventName, client, "arg2" )
                return
            end
        end

        --
        -- Do usual code for 'onRaiseTheRoof'
        --
    end
)

-- Helper function to log illegal things
function reportNaughtyness( eventName, client, reason )
    -- Report
    outputConsole( "Possible rouge client!"
            .. " client:" .. tostring(getPlayerName(client))
            .. " eventName:" .. tostring(eventName)
            .. " reason:" .. tostring(reason)
            )
end
```

</section>

------------------------------------------------------------------------

<section name="Server" class="server" show="true">
Example validation of event parameters for admin style event

``` lua
addEvent("onRequestBanPlayer", true)
addEventHandler("onRequestBanPlayer", resourceRoot,
    function(arg1, arg2)
        -- Check data is coming from a client
        if client then

            -- Check client has permission to do the deed
            if not canPlayerBan(client) then
                reportNaughtyness( eventName, client, "client" )
                return
            end

        end

        --
        -- Do usual code for 'onRequestBanPlayer'
        --
    end
)
```

</section>
Validating client ACL rights
----------------------------

In server side event handlers, always check the **'client**' global variable has permission before doing anything. This will stop hackers and script bugs from destroying your server.

Firstly, and example of BAD, INSECURE script:

<section name="Server" class="server" show="true">
BAD, INSECURE script:

``` lua
-- NO PROBLEM HERE: Command 'showgui' will only show the gui for admins
function showGui(player)
    if isObjectInGroup( player, "admin" ) then
        -- Only trigger client GUI for admins
        triggerEvent( player, "onShowGui", getResourceRootElement() )
    end
end
addCommandHandler("showgui", showGui)

-- MISTAKE HERE: Incorrectly assume onMyGuiCommand can only be called by admins
-- Script bugs and hackers mean this function can be called by anyone
function onMyGuiCommand(name)
    aclGroupAddObject(aclGetGroup("admin"), "user."..name)
    outputServerLog( "DO NOT USE THIS IS WRONG " )
end
addEventHandler("onMyGuiCommand", getResourceRootElement(), onMyGuiCommand)
```

</section>
onMyGuiCommand does not check if the sending player has permission, and is depending on code having no bugs, and no hackers in the world. Simple to fix by adding a **'client**' global variable check at the start. *(Note: checking 'source' will not fix the problem - It has to be **'client**')*

<section name="Server" class="server" show="true">
Fixed onMyGuiCommand:

``` lua
function onMyGuiCommand(name)
    -- Check 'client' really does have permission
    local clientAccountName = getAccountName( getPlayerAccount( client ) )
    if not isObjectInACLGroup ( "user." .. clientAccountName, aclGetGroup ( "Admin" ) ) ) then
        outputServerLog( "ACCESS VIOLATION by " .. getPlayerName( client ) )
        return
    end
    -- Client has permission now
    aclGroupAddObject(aclGetGroup("admin"), "user."..name)
end
addEventHandler("onMyGuiCommand", getResourceRootElement(), onMyGuiCommand)
```

</section>
