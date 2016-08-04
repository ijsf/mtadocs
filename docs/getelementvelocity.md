This function returns three floats containing the velocity (movement speeds) along the X, Y, and Z axis respectively. This means that velocity values can be positive and negative for each axis.

Syntax
------

``` lua
float float float getElementVelocity ( element theElement )
```

### Required Arguments

-   **theElement**: The [element](/docs/element.md "wikilink") you wish to retrieve the velocity of.

### Returns

If succesful, returns three *float*s that represent the element's current velocity along the *x*, *y*, and *z* axis respectively. This function can fail if the element is a player in a car. Use the vehicle element in this case. It will also fail if the element specified does not have a velocity, or does not exist. In case of failure, the first return value will be *false*.

The returned values are expressed in GTA units per 1/50th of a second[1](http://forum.mtasa.com/viewtopic.php?f=91&t=31225). A GTA Unit is equal to one metre[2](http://gta.wikia.com/Unit#GTA3.2C_GTAVC_.26_GTASA).

Example
-------

<section name="Server" class="server" show="true">
This example retrieves, calculates, and displays the speed of a random player.

``` lua
-- find a player named "someguy" and get his velocity.
speedx, speedy, speedz = getElementVelocity ( getRandomPlayer() )

-- use pythagorean theorem to get actual velocity
-- raising something to the exponent of 0.5 is the same thing as taking a square root.
actualspeed = (speedx^2 + speedy^2 + speedz^2)^(0.5) -- can be: math.sqrt(speedx^2 + speedy^2 + speedz^2)

-- multiply by 50 to obtain the speed in metres per second
mps = actualspeed * 50

-- other useful conversions
-- kilometres per hour
kmh = actualspeed * 180
-- miles per hour
mph = actualspeed * 111.847

-- report the results.
outputChatBox ( "Someguy's current velocity: " .. mps .. " metres per second." )
```

</section>
See Also
--------
