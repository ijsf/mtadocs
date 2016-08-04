This function outputs the size of garage.

Syntax
------

``` lua
float, float, float getGarageSize ( int garageID )
```

### Required Arguments

-   **garageID:** The [garage ID](/Garage.md "wikilink") that represents the garage door that is being checked.

### Returns

Returns three *float*s indicating the size of the garage.

Example
-------

<section name="Client" class="client" show="true">
This example adds the command /garagesize <garage ID>

``` lua
addCommandHandler ( "garagesize",
    function ( commandName, garageID )
        local garageID = tonumber ( garageID ) -- We convert the garage ID string to a number.
        if ( garageID ) then -- We check if garage ID is valid.
            if ( garageID >= 0 and garageID < 50 ) then -- We check if the garage ID is 0 and lower than 50 ( there's only 49 garages ).
                local x, y, z = getGarageSize ( garageID )
                if ( x and y and z ) then -- If x and y and z is valid.
                    -- We output the returned values.
                    outputChatBox ( "X: ".. x )
                    outputChatBox ( "Y: ".. y )
                    outputChatBox ( "Z: ".. z )
                else
                    outputChatBox ( "X, Y, Z values not valid" )
                end
            else
                outputChatBox ( "Garage ID must be from 0 to 49." )
            end
        else
            outputChatBox ( "You must write a garage ID" )
        end
    end
)
```

</section>
See Also
--------
