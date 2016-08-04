This function changes the maximum flying height of aircraft.

Syntax
------

``` lua
bool setAircraftMaxHeight ( float Height )
```

### Required Arguments

-   **Height** The height you want aircraft to be able to go.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example shows you a command to set your maximum aircraft height.

``` lua
function setAircraftHeight ( command, ve1 )
    local height = tonumber ( ve1 )
    if height then
        if height > 0 then
            local wert = setAircraftMaxHeight ( height )
            if wert == true then
                outputChatBox ( "Aircraft height set!", 0, 200, 0 )
            else
                outputChatBox ( "Error to set Aircraft height!", 255, 0, 0 )
            end
        else
            outputChatBox ( "Value must be above 0", 255, 0, 0 )
        end
    else
        outputChatBox ( "Error to set Aircraft height!", 255, 0, 0 )
    end
end
addCommandHandler ( "aircraft", setAircraftHeight )
```

</section>
See Also
--------
