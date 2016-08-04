<lowercasetitle/>

This function checks if an element is moving.

Syntax
------

``` lua
 bool isElementMoving ( element theElement ) 
```

### Returns

Returns true if the element is moving, false otherwise.

### Code

``` lua
function isElementMoving ( theElement )
    if isElement ( theElement ) then                     -- First check if the given argument is an element
        local x, y, z = getElementVelocity( theElement ) -- Get the velocity of the element given as argument
        return x ~= 0 or y ~= 0 or z ~= 0                -- When there is a movement on X, Y or Z return true because our element is moving
    end

    return false
end
```

### Example

<section name="Client" class="client" show="true">
This script tells the moving state to the client on the bottom left of their screen.

``` lua
local screenWidth, screenHeight = guiGetScreenSize () -- Get the screen resolution (width and height)

function idleCheck ()
    local state   = "Unknown"
    local element = getPedOccupiedVehicle ( localPlayer ) or localPlayer

    -- Check whether the player is moving or not.
    if isElementMoving ( element ) then
        state = "moving"
    else
        state = "idling"
    end

    -- Write our state string to the lower left corner of the screen
    dxDrawText ( "You are " .. state .. "!", 40, screenHeight - 40, screenWidth, screenHeight, tocolor ( 255, 255, 255, 255 ), 1, "default" )
end

-- Keep the text visible with onClientRender.
addEventHandler ( "onClientRender", root, idleCheck )
```

</section>
See Also
--------
