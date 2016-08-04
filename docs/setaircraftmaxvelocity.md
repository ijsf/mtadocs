Syntax
------

``` lua
bool setAircraftMaxVelocity ( float velocity )
```

### Required Arguments

-   **velocity:** The max velocity, can be 0 or any positive value. Default is **1.5**.

### Returns

Returns true if the max velocity was set correctly, false otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example will increase or decrease the max velocity by pressing numpad keys + or -.

``` lua
function handleKeyboard( key, state )

    if state then

        if key == "num_add" then

            local fMaxVelocity = getAircraftMaxVelocity() + 0.1

            if setAircraftMaxVelocity( fMaxVelocity ) then
                outputChatBox( string.format( "Max velocity set to %.1f", fMaxVelocity ))
            else
                outputChatBox( string.format( "Unable to set max velocity to %.1f", fMaxVelocity ) )
            end

        elseif key == "num_sub" then

            local fMaxVelocity = getAircraftMaxVelocity() - 0.1

            if setAircraftMaxVelocity( fMaxVelocity ) then
                outputChatBox( string.format( "Max velocity set to %.1f", fMaxVelocity ) )
            else
                outputChatBox( string.format( "Unable to set max velocity to %.1f", fMaxVelocity ) )
            end
        end
    end
end

addEventHandler( "onClientKey", root, handleKeyboard )
```

</section>
<section name="Server" class="server" show="true">
This example will double the max velocity for everyone when the resource is started.

``` lua
function handleResourceStart( )
    setAircraftMaxVelocity( 3 )
end
addEventHandler( "onResourceStart",  resourceRoot, handleResourceStart )
```

</section>
See Also
--------
