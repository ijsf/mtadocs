<lowercasetitle></lowercasetitle>

This Function get a number of the players in a marker.

Syntax
------

``` lua
int getPlayersInMarker(marker yourmarker)
```

### Required Arguments

-   **yourmarker:** the marker to get the count from it.

### Returns

Return a number of players in the marker.

Code
----

<section name="Function source" class="server" show="true">
``` lua
function getPlayersInMarker(marker)
    local players = 0
    if marker and getElementType(marker) == "marker" then
        for i,player in ipairs(getElementsByType("player")) do
            if isElementWithinMarker(player,marker) then
                players = players + 1
            end
        end
    end
    return players
end
```

</section>
Example
-------

<section name="Example" class="server" show="true">
``` lua
mark = createMarker(123.23432,12.4324,3.0023,"cylinder",5,255,0,0)

addCommandHandler("count",
    function (player)
        local count = getPlayersInMarker(mark)
        outputChatBox("There is " .. count .. " in the marker",player)
    end
)
```

</section>
Created By **|Mr|-Talal07-|**.

See Also
--------
