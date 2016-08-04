Syntax
------

``` lua
bool setWorldSoundEnabled( int group, [ int index = -1, ] bool enable )
```

### Required Arguments

-   **group :** An integer representing the world sound group
-   **enable :** Set *false* to disable, *true* to enable

### OptionalArguments

-   **index :** An integer representing an individual sound within the group

### Returns

Returns *true* if the world sound was correctly enabled/disabled, *false* if invalid values were passed.

Example
-------

This is a simplified example that lets the client toggle their weapon sounds.

``` lua
function toggleWeaponSounds_f ( )
    local enabled = isWorldSoundEnabled ( 5 ) -- We place this variable here for checking.
    enabled       = not enabled -- And here we invert (toggle) the variable, so if it's false, it becomes true, if it's true, it becomes false.
    -- Used for the chat declaration:
    local state   = "enabled"

    if ( not enabled ) then
        state = "disabled"
    end
    --

    setWorldSoundEnabled ( 5, enabled ) -- And here the toggling happens.
    outputChatBox ( "Weapon sounds " .. state )
end
addCommandHandler ( "toggleweaponsounds", toggleWeaponSounds_f )
```

Requirements
------------

See Also
--------
