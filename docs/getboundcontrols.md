<lowercasetitle></lowercasetitle>

Returns a list of control names that are bound to the specified key.

Syntax
------

``` lua
table getBoundControls ( string key )
```

### Required Arguments

-   **key:** The name of the key. See [Key names](/docs/key_names.md "wikilink").

### Returns

If one or more controls are bound to the specified key, a table is returned containing the names of all the bound controls. If no controls are bound or an invalid name was passed, returns empty *table*.

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
local controlTable = { "fire", "next_weapon", "previous_weapon", "forwards", "backwards", "left", "right", "zoom_in", "zoom_out",
 "change_camera", "jump", "sprint", "look_behind", "crouch", "action", "walk", "aim_weapon", "conversation_yes", "conversation_no",
 "group_control_forwards", "group_control_back", "enter_exit", "vehicle_fire", "vehicle_secondary_fire", "vehicle_left", "vehicle_right",
 "steer_forward", "steer_back", "accelerate", "brake_reverse", "radio_next", "radio_previous", "radio_user_track_skip", "horn", "sub_mission",
 "handbrake", "vehicle_look_left", "vehicle_look_right", "vehicle_look_behind", "vehicle_mouse_look", "special_control_left", "special_control_right",
 "special_control_down", "special_control_up" }

function getBoundControls (key)
    local controls = {}
    for _,control in ipairs(controlTable) do
        for k in pairs(getBoundKeys(control)) do
            if (k == key) then
                controls[control] = true
            end
        end
    end
    return controls
end
```

Author: Lex128

</section>
Example 1
---------

This code adds a special action when activated detonator and blocks its actual use in the game.

``` lua
function detonatorAction (key, state)
    if (getPedWeapon (localPlayer) ~= 40) then return end          -- make sure that the detonator is in the hands of

    outputChatBox ("Whohooo... BOOM!", 255, 0, 0)                  -- make necessary actions
    for control in pairs (getBoundControls(key)) do
        setControlState (control, false)
    end
end

bindKey ("mouse1", "down", detonatorAction)
```

Example 2
---------

This code checks if someone has 'sprint' bound onto the mouse wheel (a well-known glitch which is now disabled by default) and kicks a player for having it bound

<section name="Clientside" class="client" show="true">
``` lua
function onStart()
    if ( (getBoundControls("mouse_wheel_up")["sprint"]) or (getBoundControls("mouse_wheel_down")["sprint"]) ) then
        triggerServerEvent("kickPlayerForCheating", root, "supersprint binds")
    end
end
addEventHandler("onClientResourceStart", resourceRoot, onStart)
```

</section>
<section name="Serverside" class="server" show="true">
``` lua
addEvent("kickPlayerForCheating", true)
addEventHandler("kickPlayerForCheating", root, function(cheat)
    kickPlayer(client, "Anti Cheat", "Cheat detected: "..cheat)
end)
```

</section>
See Also
--------
