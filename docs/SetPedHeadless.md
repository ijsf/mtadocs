With this function, you can set if a ped has a head or not.

Syntax
------

``` lua
bool setPedHeadless  ( ped thePed, bool headState )
```

### Required Arguments

-   **thePed**: The [ped](/ped.md "wikilink") to check.
-   **headState**: head state, use true if you want the ped be headless, use false to give back the head.

### Returns

Returns *true* if successful, *false* otherwise

Example
-------

<section name="Server" class="server" show="true">
This example enables a player to behead themselves, and give them their head back.

``` lua
function removeMyHead(thePlayer)
    setPedHeadless(thePlayer, true) -- Removes the players head
    outputChatBox("You have been beheaded!", thePlayer, 255, 0, 0) -- A confirmation message for the player
end
addCommandHandler("beheadme", removeMyHead)

function giveBackHead(thePlayer)
    setPedHeadless(thePlayer, false) -- Gives the player a head
    outputChatBox("You have been given a head!", thePlayer, 255, 0, 0) -- A confirmation message for the player
end
addCommandHandler("headmeup", giveBackHead)
```

</section>
See Also
--------

[ru:setPedHeadless](/ru:setPedHeadless.md "wikilink")
