<lowercasetitle></lowercasetitle>

This function takes a set of XY coordinates, a distance and a rotation argument. It returns XY coordinates of the point that is the given distance away from the given point, in the given direction.

Syntax
------

``` lua
float, float getPointFromDistanceRotation(float x, float y, float dist, float angle)
```

### Required Arguments

-   **x**: The X coordinate of the starting point.
-   **y**: The Y coordinate of the starting point.
-   **dist**: The distance from the starting point to the target point.
-   **angle**: The direction from the starting point to the target point.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getPointFromDistanceRotation(x, y, dist, angle)

    local a = math.rad(90 - angle);
 
    local dx = math.cos(a) * dist;
    local dy = math.sin(a) * dist;
 
    return x+dx, y+dy;
 
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This command surrounds a player with peds.

``` lua
addCommandHandler("surround",
function (player)

  local x,y,z = getElementPosition(player);

  for i=1, 8 do
    local newX, newY = getPointFromDistanceRotation(x, y, 2, 360 * (i/8));
    createPed(10, newX, newY, z)
  end

end
);
```

</section>
Author: robhol.

See Also
--------
