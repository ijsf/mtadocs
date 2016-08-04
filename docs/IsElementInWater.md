This function checks whether an [element](/docs/element.md "wikilink") is submerged in water.

Syntax
------

``` lua
bool isElementInWater ( element theElement )
```

### Required Arguments

-   **theElement**: The element to check.

### Returns

Returns *true* if the passed element is in water, *false* if it isn't, or if the element is invalid.

Example
-------

Creates a command that checks if the player is in water or not.

<section name="Server" class="server" show="true">
``` lua

function waterCheck(thePlayer)
    if isElementInWater(thePlayer) then
        outputChatBox("Wet.", thePlayer)
    else
        outputChatBox("Dry.", thePlayer)
    end
end

addCommandHandler("check", waterCheck)
```

</section>
Function which checks if player is in water, which is triggered when player dies.

<section name="Client" class="client" show="true">
``` lua
function diedInWater()
   if isElementInWater(source) then
       local name = source == localPlayer and "You are" or getPlayerName(source).." is"
       outputChatBox(name.." sleeping with the fishies!")
   end
end
addEventHandler("onClientPlayerWasted", root, diedInWater)
```

</section>
Function which checks if player is in water and then kills the player after 3 seconds.

<section name="Client" class="client" show="true">
``` lua
addEventHandler ("onClientResourceStart", resourceRoot,
function()
    setTimer(function()
                if isElementInWater( localPlayer ) then
                    setElementHealth( localPlayer, 0 )
                 end
             end,
             3000, 0 )
end
)
```

</section>
See Also
--------
