This function returns the alpha (transparency) value for the specified [element](/docs/element.md "wikilink"). This can be a [player](/docs/player.md "wikilink"), [ped](/docs/ped.md "wikilink"), [object](/docs/object.md "wikilink"), [vehicle](/docs/vehicle.md "wikilink") or [weapon](/docs/element/weapon.md "wikilink").

Syntax
------

``` lua
int getElementAlpha ( element theElement )
```

### Required Arguments

-   **theElement:** The [element](/docs/element.md "wikilink") whose alpha you want to retrieve.

### Returns

Returns an integer (0-255; 0 = transparent) indicating the element's alpha, or *false* if invalid arguments were passed.

Example
-------

<section name="Clientside example" class="client" show="true">
This example outputs whether the player is invisible.

``` lua
function amIVisible()
    if getElementAlpha(localPlayer) == 0 then
            outputChatBox("I'm invisible")
        else
            outputChatBox("I'm not invisible")
        end
end
addCommandHandler ( "amivisible", amIVisible )
```

</section>
See Also
--------
