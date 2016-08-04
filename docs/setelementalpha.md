This function sets the alpha (transparency) value for the specified [element](/docs/element.md "wikilink"). This can be a [player](/player.md "wikilink"), [ped](/ped.md "wikilink"), [object](/object.md "wikilink"), [vehicle](/vehicle.md "wikilink") or [weapon](/Element/Weapon.md "wikilink").

Syntax
------

``` lua
bool setElementAlpha ( element theElement, int alpha )
```

### Required Arguments

-   **theElement:** The [element](/docs/element.md "wikilink") whose alpha you want to set.
-   **alpha:** The alpha value to set. Values are 0-255, where 255 is fully opaque and 0 is fully transparent.
    -   **Note:** [Objects](/docs/Object.md "wikilink") are fully transparent at 140.

### Returns

Returns *true* or *false* if invalid arguments were passed.

Example
-------

<section name="Clientside example" class="client" show="true">
This example makes the player invisible.

``` lua
function invisible()
        setElementAlpha(localPlayer, 0)
end
addCommandHandler ( "invisible", invisible )
```

</section>
<section name="Serverside example" class="server" show="true">
This example lets you toggle invisibility when you write /invis.

``` lua
function toggleInvis ( thePlayer )  -- thePlayer is whoever executed the command
        if getElementAlpha( thePlayer ) == 0 then       -- if the player is NOT invisible
        setElementAlpha ( thePlayer, 0 )    -- set the players alpha to 0 (make them invisible)
    else            -- else, if the source player IS visible
        setElementAlpha ( thePlayer, 255 )  -- set the players alpha to 255 (make them 100% visible)
    end
end
addCommandHandler ( "invis", toggleInvis )  -- When /invis is typed, the function 'toggleInvis' will start.
```

</section>
See Also
--------
