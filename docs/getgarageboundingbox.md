This function outputs the bounding box of a garage.

Syntax
------

``` lua
float, float, float, float getGarageBoundingBox ( int garageID )
```

### Required Arguments

-   **garageID:** The [garage ID](/docs/Garage.md "wikilink") that represents the garage door that is being checked.

### Returns

Returns four *float*s indicating the bounding box of the garage. *Western X position, Eastern X position, Southern Y position, Northern Y position.*

Example
-------

<section name="Client" class="client" show="true">
Checks if the player is inside the bounding box of the garage and outputs the result to the chat

``` lua
function garageCheck ( command, garageID )
    if not garageID then
        return
    end
    
    local west, east, south, north = getGarageBoundingBox ( garageID ) --get the bounding box of the specified garage
    local x, y, z = getElementPosition ( getLocalPlayer ( ) ) --get the position of the player
    
    if x > west and x < east and y > south and y < north then --check if the player is inside the bounding box
        outputChatBox ( "You are inside the garage" )
    else
        outputChatBox ( "You are outside the garage" )
    end
end

addCommandHandler ( "garagecheck", garageCheck )
```

</section>
See Also
--------
