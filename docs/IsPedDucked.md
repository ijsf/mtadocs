This function checks if the specified [ped](/docs/ped.md "wikilink") is ducked (crouched) or not.

Syntax
------

``` lua
bool isPedDucked ( ped thePed )
```

### Required Arguments

-   **thePed**: The [ped](/docs/ped.md "wikilink") to check.

### Returns

Returns *true* if the ped is ducked, *false* otherwise.

Example
-------

<section class="client" name="Client" show="true">
This example checks if a random player is ducked or not, and if so displays a message in the chat box.

``` lua
local players = getElementsByType ( "player" )
local randomPlayer = players[math.random(#players)]
if isPedDucked ( randomPlayer ) then
    outputChatBox ( getPlayerName ( randomPlayer ) .. " is currently crouching." )
end
```

This example creates a function that lets you toggle the crouching state of a ped.

``` lua
function setPedDucked(ped, bool)
    local alreadyDucked = isPedDucked(ped)
    if (alreadyDucked and not bool) then
        if (ped == localPlayer) then
            setControlState("crouch", true)
            setTimer(setControlState, 50, 1, "crouch", false)
        else
            setPedControlState(ped, "crouch", true)
            setTimer(setPedControlState, 50, 1, ped, "crouch", false)
        end
        return true
    elseif (not alreadyDucked and bool) then
        if (ped == localPlayer) then
            setControlState("crouch", true)
            setTimer(setControlState, 50, 1, "crouch", false)
        else
            setPedControlState(ped, "crouch", true)
            setTimer(setPedControlState, 50, 1, ped, "crouch", false)
        end
        return true
    end
    return false
end
```

</section>
[ru:IsPedDucked](/docs/ru:IsPedDucked.md "wikilink")

See Also
--------
