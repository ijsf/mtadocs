This function lets you get an RG Color depending on the percentage.

Syntax
------

``` lua
int, int getRGColorFromPercentage ( int percentage )
```

### Required Arguments

-   **percentage:** The value which you want to get the RG from. It must be between 0 and 100.

### Returns

Returns two integers, with red, and green values if percentage goes between 0 and 100. Returns false otherwise.

Code
----

<section name="Server/Client-Side Script" class="both" show="true">
    function getRGColorFromPercentage(percentage)
        if not percentage or
            percentage and type(percentage) ~= "number" or
            percentage > 100 or percentage < 0 then
            outputDebugString( "Invalid argument @ 'getRGColorFromPercentage'", 2 )
            return false
        end

        if percentage > 50 then
            local temp = 100 - percentage
            return temp*5.1, 255
        elseif percentage == 50 then
            return 255, 255
        end
        
        return 255, percentage*5.1
    end

</section>
Example
-------

<section name="Client-Side Example" class="client" show="true">
This example shows the vehicle health with a different color depending on its health in the bottom part of the screen.

``` lua
local sW, sH = guiGetScreenSize()

function showHealth()
    local veh = getPedOccupiedVehicle(localPlayer)
    if not veh then return end

    local health = getElementHealth(veh) - 250
    -- When the car has got a health of 250, it turns into fire, so we remove 250 of the original health in order not to take it into account.
    if health < 0 then health = 0 end -- In case it goes negative, we set it as if it were 0.
    -- Now we need to make the conversion to a number between 0 to 100 knowing that health goes from 0 to 750.
    local percentage = math.floor((health*0.133333333333)+0.5) -- Transformation into percentage.
    -- We now use the function
    local r, g = getRGColorFromPercentage(percentage)
    -- We show it
    dxDrawText("Health: "..percentage.."%", sW/2-100, sH-45, sW/2+100, sH-15, tocolor(r, g, 0, 255), 1, "default", "center", "center")
end
 
-- We add the handler of the function when player enters a car.
addEventHandler("onClientPlayerVehicleEnter", localPlayer, 
    function()
        addEventHandler("onClientPreRender", root, showHealth)
    end
)

-- We remove it when the player leaves a car.
addEventHandler("onClientPlayerVehicleExit", localPlayer, 
    function()
        removeEventHandler("onClientPreRender", root, showHealth)
    end
)
```

</section>
**Author: Renkon**

See Also
--------

[:Category:Useful\_Functions](/docs/:Category:Useful_Functions.md "wikilink")
