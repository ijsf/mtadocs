This function allows you to set **moving** element speed in kph or mph units.

Syntax
------

``` lua
bool setElementSpeed (element theElement, [ int/string unit="kph", int speed=0 ])
```

### Required Arguments

-   **theElement**: Element you want to set speed of

### Optional Arguments

-   **unit**: Units in which speed should be set. This can be 1 or “mph” for mph, any other value for kph.
-   **speed**: Speed in selected unit

Code
----

<section name="Function source" class="both" show="true">
``` lua
function setElementSpeed(element, unit, speed)
    if (unit == nil) then unit = 0 end
    if (speed == nil) then speed = 0 end
    speed = tonumber(speed)
    local acSpeed = getElementSpeed(element, unit)
    if (acSpeed~=false) then -- if true - element is valid, no need to check again
        local diff = speed/acSpeed
        if diff ~= diff then return end -- if the number is a 'NaN' return end.
        local x,y,z = getElementVelocity(element)
        setElementVelocity(element,x*diff,y*diff,z*diff)
        return true
    end

    return false
end
```

</section>
Example
-------

<section name="Server-side example" class="server" show="true">
This example adds command that set player vehicle speed to provided one (in predefined unit kph). Note: It doesn't care if player is driver or passenger.

``` lua
addCommandHandler("setmyspeed",
function (player, cmd, arg1)
  local veh = getPedOccupiedVehicle(player)
  if (veh) then
    setElementSpeed(veh, "kph", tonumber(arg1))
  else
    outputChatBox("You have to sit in vehicle", player)
  end
end
)
```

</section>
By **varez**.

See Also
--------
