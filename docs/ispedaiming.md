This function checks if a ped is aiming. Returns true if yes and false if not.
**Important : ONLY WORKS CLIENT SIDE.**

Syntax
------

``` lua
bool isPedAiming ( ped thePedToCheck )
```

### Required Arguments

-   **thePedToCheck**: The ped element.

### Returns

Returns true if ped is aiming a weapon, false if not.

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
function isPedAiming ( thePedToCheck )
    if isElement(thePedToCheck) then
        if getElementType(thePedToCheck) == "player" or getElementType(thePedToCheck) == "ped" then
            if getPedTask(thePedToCheck, "secondary", 0) == "TASK_SIMPLE_USE_GUN" then
                return true
            end
        end
    end
    return false
end
```

</section>
Example
-------

The example outputs if the player is aiming a gun when the player presses b.

``` lua
function checkAim()
    if isPedAiming(localPlayer) then
        outputChatBox("Aiming")
    else
        outputChatBox("Not aiming")
    end
end
bindKey("b", "down", checkAim)
```

See Also
--------
