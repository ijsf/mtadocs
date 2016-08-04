This function return the number of players that are within certain range of specific position .

Syntax
------

``` lua
int countPlayersInRange(float x, float y, float z, float range)
```

### Required Arguments

-   **x** : The x coordinate of the destination .
-   **y** : The y coordinate of the destination .
-   **z** : The z coordinate of the destination .
-   **range** : Range size .

Code
----

<section name="Function source" class="both" show="true">
``` lua
function countPlayersInRange(x, y, z, range)
    if tonumber(x..y..z..range) then
        local add = 0
        for _, v in ipairs(getElementsByType("player")) do
            local px, py, pz = getElementPosition( v )
            if getDistanceBetweenPoints3D(px, py, pz, tonumber(x), tonumber(y), tonumber(z)) <= tonumber(range) then
                add = add + 1
            end
        end
        return add
    else
        return false
    end
end
```

</section>
Example
-------

<section name="Server Side [Example]" class="server" show="true">
This Example get players in range and out put it in chat .

``` lua
addCommandHandler('EH10',
function (player)
    local number = countPlayersInRange(x, y, z, range)
        outputChatBox("Number : " .. number .. " .", player, 255, 0, 0, true)
    end
)
```

</section>
-   \[ Created By ; EH10 \]

Skype ; maxurmaxur

See Also
--------
