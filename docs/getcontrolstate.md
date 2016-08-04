This function will check if a player is pressing a particular control. Controls are those that affect GTA. If you wish to get the state of another key, use [bindKey](/docs/bindKey.md "wikilink") and a command function.

Note: Not all control states are sent to the server at all times, as such their state may be given incorrectly. As a rule, keys that move or affect the player or their vehicle are most likely to be accurate. For increased accuracy (and also increased bandwidth usage) use bindKey instead to bind a GTA control name to a function.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool getControlState ( player thePlayer, string controlName )
```

### Required Arguments

-   **thePlayer:** The player you wish to get the control state of. Do not use this parameter when scripting for client.
-   **controlName:** The control that you want to get the state of. See [control names](/docs/control_names.md "wikilink") for a list of possible controls.

**Note:** several controls are not synched with the server, therefore the function will always return *false* for these controls serverside. These controls are:

-   next\_weapon
-   previous\_weapon
-   jump
-   zoom\_in
-   zoom\_out
-   look\_behind
-   change\_camera
-   conversation\_yes
-   conversation\_no
-   group\_control\_forwards
-   group\_control\_back
-   sub\_mission
-   radio\_next
-   radio\_previous
-   vehicle\_look\_left
-   vehicle\_look\_right
-   vehicle\_look\_behind
-   vehicle\_mouse\_look
-   special\_control\_\*

</section>
<section name="Client" class="client" show="true">
``` lua
bool getControlState ( string controlName ) 
```

### Required Arguments

-   **controlName:** The control that you want to get the state of. See [control names](/docs/control_names.md "wikilink") for a list of possible controls.

</section>
### Returns

Returns the state of the control, *false* if the control doesn't exist or if the player is dead.

Example
-------

<section name="Server" class="server" show="true">
This example starts a repeating check when a player spawns, if a player presses the fire key, they'll be killed.

``` lua
function onPlayerSpawn ( theSpawnpoint )
    killPlayerIfTheyPressThisKey ( source, "fire" ) -- start a repeating check
end
addEventHandler ( "onPlayerSpawn", root, onPlayerSpawn )

function killPlayerIfTheyPressThisKey ( thePlayer, key )
    if ( getControlState ( thePlayer, key ) ) then        -- if they're pressing the fire key
        outputChatBox ( "Violence will not be tolerated!", thePlayer )
        killPed ( thePlayer )                          -- kill them
    else                                                  -- otherwise..
        setTimer ( killPlayerIfTheyPressThisKey, 500, 1, thePlayer, key ) -- call this function again in 500ms
    end
end
```

</section>
See Also
--------
