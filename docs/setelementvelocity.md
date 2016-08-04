This function sets the velocity (movement speeds) along each axis, for an element.

This is not compatible with all elements. Only the following elements are compatible:

-   [Peds](/docs/ped.md "wikilink").
-   [Vehicles](/docs/vehicle.md "wikilink").
-   [Objects](/docs/object.md "wikilink").
-   [Projectiles](/docs/projectile.md "wikilink").

Syntax
------

``` lua
bool setElementVelocity ( element theElement, float speedX, float speedY, float speedZ )
```

### Required Arguments

-   **theElement:** The [element](/docs/element.md "wikilink") you wish to set the velocity of.
-   **speedX:** A floating point value determining the speed along the X axis.
-   **speedY:** A floating point value determining the speed along the Y axis.
-   **speedZ:** A floating point value determining the speed along the Z axis.

### Returns

Returns *true* if the speed was set successfully, *false* if a bad element was specified or other bad arguments.

Example
-------

<section class="server" name="Server" show=true>
This example adds a function which copies the speed of a random player to another random player. If there are less than 2 players it returns *false*.

``` lua
function equalTwoRandomPlayersVelocity()
    if getPlayerCount() < 2 then -- If there's only one player (or no players) this doesn't make sense
        return false
    end
    local randomPlayer1, randomPlayer2 = getRandomPlayer(), getRandomPlayer() -- Get two random players
    while randomPlayer1 == randomPlayer2 do -- Make sure the two players are different
        randomPlayer2 = getRandomPlayer()
    end
    local speedx, speedy, speedz = getElementVelocity (randomPlayer1) -- Get the velocity of the first random player
    setElementVelocity(randomPlayer2, speedx, speedy, speedz) -- Copy that velocity to the second random player
    outputChatBox("Now " .. getPlayerName(randomPlayer2) .. " runs as fast as " .. getPlayerName(randomPlayer1) .. "!", root, 255, 128, 0)
    return true
end
```

</section>
See Also
--------
