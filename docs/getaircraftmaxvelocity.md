Syntax
------

``` lua
float getAircraftMaxVelocity ()
```

### Returns

Returns a float being the max velocity that is currently set, depending on which side it is used.

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
This example will tell the max velocity to everyone when the resource is started.

``` lua
function handleResourceStart( )
    outputChatBox( string.format( "Server's aircraft max velocity is set to %.1f", getAircraftMaxVelocity() ) )
end
addEventHandler( "onResourceStart", resourceRoot, handleResourceStart )
```

</section>
See Also
--------
