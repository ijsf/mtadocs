This function outputs X, Y and Z position of given garage.

Syntax
------

``` lua
float, float, float getGaragePosition ( int garageID )
```

### Required Arguments

-   **garageID:** The [garage ID](/Garage.md "wikilink") that represents the garage door that is being checked.

### Returns

Returns three *float*s indicating the position of the garage, *x*, *y* and *z* respectively.

Example
-------

<section name="Client" class="client" show="true">
This element has to create a blip at the nearest garage and removes it in 10 seconds.

``` lua
function getNearestGarageFromElement (element)
  nearestID = -1
  nearestDistance = 999999999999
  local ex,ey,ez = getElementPosition (element)
  for i=0,49 do
    local x,y,z = getGaragePosition (i)
    if (getDistanceBetweenPoints3D (ex,ey,ez,x,y,z) < nearestDistance) then
      nearestID = i
      nearestDistance = getDistanceBetweenPoints3D (ex,ey,ez,x,y,z)
    end
  end
  local _nearestID = nearestID
  nearestID = nil
  return _nearestID
end

addCommandHandler ("findgarage",
function(command)
  local garageID = getNearestGarageFromElement (getLocalPlayer())
  if (garageID ~= -1) then
    local x,y,z = getGaragePosition (garageID)
    local garageBlip = createBlip (x,y,z,41)
    setTimer (
      function (garageBlip)
        destroyElement (garageBlip)
      end
    ,10000,1,garageBlip)
  end
end)
```

</section>
See Also
--------

[Category:Needs\_More\_Examples](/Category:Needs_More_Examples.md "wikilink")
