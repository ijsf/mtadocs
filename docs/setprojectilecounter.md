Will change the projectile counter timer which depending on the projectile type will do different things:

-   Rockets and Grenades will explode when it hits 0
-   Teargas may be a duration timer
-   Satchels restart (we currently assume it doesn't cause an effect)
-   Molotov will explode with search ground level when it hits 0

Syntax
------

``` lua
bool setProjectileCounter ( projectile projectile, int timeToDetonate )
```

### Required Arguments

-   **projectile:** The projectile to edit the timer of.
-   **timeToDetonate:** The time in milliseconds to detonation.

### Returns

Returns *true* on success, *false* otherwise.

### Example

<section name="Client" class="client" show="true">
With this example you can use /setbombtime to set a delay duration of a projectile explosion.

``` lua
function changeProjectileDelay( cmd, bombIndex, duration )
    local bombIndex = tonumber( bombIndex ) or nil
    local duration = tonumber( duration ) or nil
    
    if ( bombIndex ) and ( duration ) then
        local found = false

        for index,projectile in ipairs( getElementsByType( "projectile" ) ) do
            if ( index == bombIndex ) then
                if ( setProjectileCounter( projectile, duration * 1000 ) ) then
                    outputChatBox( "Projectile (" .. index .. ") detonates in " .. duration .. " seconds.", 0, 255, 0, false )
                else
                    outputChatBox( "Something went wrong when setting the duration.", 255, 0, 0, false )
                end

                found = true
                break
            end
        end

        if ( not found ) then
            outputChatBox( "Projectile with index " .. bombIndex .. " was not found.", 255, 0, 0, false )
        end
    else
        outputChatBox( "SYNTAX: /" .. cmd .. " [bomb index] [duration in seconds]", 220, 180, 0, false )
    end
end
addCommandHandler( "setbombtime", changeProjectileDelay )
```

</section>
Requirements
------------

See Also
--------
