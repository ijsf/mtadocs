<lowercasetitle></lowercasetitle>

These useful clientside functions bind the keys bound to a control individually, using [bindKey](/docs/bindKey.md "wikilink"), and unbind them using [unbindKey](/unbindKey.md "wikilink"). The objective of these functions is to bypass the limitation of binding a control directly which ignores key presses if the control is deactivated at the moment (so the script would be able to react if the player presses *aim\_weapon* in a vehicle, for example).

Syntaxes
--------

``` lua
boolean/nil bindControlKeys ( string control, misc bindData )
```

``` lua
boolean/nil unbindControlKeys ( string control )
```

### Required arguments

-   **control:** The name of the control to bind or unbind. See [control names](/docs/control_names.md "wikilink").
-   **bindData:** (*bindControlKeys* only) Configures how the control keys will be bound. See clientside [bindKey](/docs/bindKey.md "wikilink") syntaxes for reference.

### Returns

These functions return *true* if no error arised. They return *nil* plus an error message otherwise.

Restrictions
------------

**You can only have one control keys bind per control**. That should be enough for most scripts. If you want to create more binds, copy these functions into a new script file (or [resource](/docs/resource.md "wikilink")) and mark them as *local*.

Functions source
----------------

<section name="Clientside script" class="client" show="true">
``` lua
local controls = { "fire", "next_weapon", "previous_weapon", "forwards", "backwards", "left", "right", "zoom_in", "zoom_out",
 "change_camera", "jump", "sprint", "look_behind", "crouch", "action", "walk", "aim_weapon", "conversation_yes", "conversation_no",
 "group_control_forwards", "group_control_back", "enter_exit", "vehicle_fire", "vehicle_secondary_fire", "vehicle_left", "vehicle_right",
 "steer_forward", "steer_back", "accelerate", "brake_reverse", "radio_next", "radio_previous", "radio_user_track_skip", "horn", "sub_mission",
 "handbrake", "vehicle_look_left", "vehicle_look_right", "vehicle_look_behind", "vehicle_mouse_look", "special_control_left", "special_control_right",
 "special_control_down", "special_control_up" }

local boundControlsKeys = {}
local bindsData = {}

function unbindControlKeys(control)
    -- Ensure the argument has got the appropiate type
    assert(type(control) == "string", "Bad argument @ unbindControlKeys [string expected, got " .. type(control) .. "]")
    -- Check if we have a valid control
    local validControl
    for _, controlComp in ipairs(controls) do
        if control == controlComp then
            validControl = true
            break
        end
    end
    assert(validControl, "Bad argument @ unbindControlKeys [Invalid control name]")
    -- Have we got a bind on this control?
    assert(boundControlsKeys[control], "Bad argument @ unbindControlKeys [There is no bind on such control]")
    -- Unbind each key of the control
    for _, bindData in pairs(bindsData[control]) do
        unbindKey(unpack(bindData))
    end
    -- Remove references
    boundControlsKeys[control] = nil
    bindsData[control] = nil
    return true
end

function bindControlKeys(control, ...)
    -- Ensure the argument has got the appropiate type
    assert(type(control) == "string", "Bad argument 1 @ bindControlKeys [string expected, got " .. type(control) .. "]")
    -- Check if we have a valid control
    local validControl
    for _, controlComp in ipairs(controls) do
        if control == controlComp then -- Is the specified control in the table?
            validControl = true -- If so, it's a valid control
            break
        end
    end
    assert(validControl, "Bad argument 1 @ bindControlKeys [Invalid control name]")
    -- Do we already have this control bound?
    if boundControlsKeys[control] then
        unbindControlKeys(control) -- Delete the first control keys bind
    end
    boundControlsKeys[control] = getBoundKeys(control) -- Store the keys of that control that will be bound
    bindsData[control] = {} -- Store bind data, so we can unbind each key of the control later
    for key in pairs(boundControlsKeys[control]) do
        -- Can we bind the key with the specified arguments?
        assert(bindKey(key, unpack(arg)), "Bad arguments @ bindControlKeys [Could not create key bind]")
        -- If so, register the bind data and continue
        table.insert(bindsData[control], { key, unpack(arg) })
    end
    return true
end

-- The keys bound to a control can be changed in Settings. The next function updates the binds properly in that case.
-- Also note that the next function IS NOT MEANT to be exported or called by the script.
local function keepControlKeyBindsAccurate()
    if next(boundControlsKeys) then -- Have we got any control keys bound?
        for boundControl, boundKeys in pairs(boundControlsKeys) do
            if toJSON(boundKeys) ~= toJSON(getBoundKeys(boundControl)) then -- Have we changed the keys bound to a control?
                -- Update our custom control bind
                for _, bindData in ipairs(bindsData[boundControl]) do
                    unbindKey(unpack(bindData)) -- Unbind every key of that cotnrol that we have bound before
                    -- Bind again the appropiate keys
                    for key in pairs(getBoundKeys(boundControl)) do
                        local bindDataNoKey = bindData -- Copy bindData into another variable
                        table.remove(bindDataNoKey, 1) -- Ignore the key of our bindData
                        bindKey(key, unpack(bindDataNoKey)) -- Bind again the data, but with the updated key
                        bindData[1] = key -- Update the key in the references
                    end
                end
                boundControlsKeys[boundControl] = getBoundKeys(boundControl) -- Update the control bound keys list
            end
        end
    end
end
addEventHandler("onClientRender", root, keepControlKeyBindsAccurate)
```

</section>
Example
-------

This example allows players to toggle driveby by pressing or releasing the *aim\_weapon* control.

``` lua
local function toggleDriveby()
    if isPedInVehicle(localPlayer) then
        setPedDoingGangDriveby(localPlayer, not isPedDoingGangDriveby(localPlayer))
    end
end
bindControlKeys("aim_weapon", "both", toggleDriveby)
```

See also
--------
