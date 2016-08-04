This function creates a [blip](/docs/blip.md "wikilink") that is attached to an [element](/element.md "wikilink"). This blip is displayed as an icon on the client's radar and will 'follow' the element that it is attached to around.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
blip createBlipAttachedTo ( element elementToAttachTo [, int icon = 0, int size = 2, int r = 255, int g = 0, int b = 0, int a = 255, int ordering = 0, float visibleDistance = 99999.0, visibleTo = getRootElement( ) ] )
```

</section>
<section name="Client" class="client" show="true">
``` lua
blip createBlipAttachedTo ( element elementToAttachTo [, int icon = 0, int size = 2, int r = 255, int g = 0, int b = 0, int a = 255, int ordering = 0, float visibleDistance = 99999.0] )
```

</section>
### Required Arguments

-   **elementToAttachTo:** The [element](/docs/element.md "wikilink") to attach the marker to.

### Optional Arguments

-   **icon:** The icon that the radar blips should be. Valid values can be seen at [Blip Icons](/docs/Blip_Icons.md "wikilink")
-   **size:** The size of the radar blip. Only applicable to the *Marker* icon. Default value is 2.
-   **r:** The amount of red in the blip's color (0 - 255). Only applicable to the *Marker* icon. Default is 255.
-   **g:** The amount of green in the blip's color (0 - 255). Only applicable to the *Marker* icon. Default is 0.
-   **b:** The amount of blue in the blip's color (0 - 255). Only applicable to the *Marker* icon. Default is 0.
-   **a:** The amount of alpha in the blip's color (0 - 255). Only applicable to the *Marker* icon. Default is 255.

<section name="Server" class="server" show="true">
-   **visibleTo:** What elements can see the blip. Defaults to visible to everyone. See [visibility](/docs/visibility.md "wikilink").

</section>
### Returns

Returns a [blip](/docs/blip.md "wikilink") if the blip was created succesfully, or *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example creates a radar blip attached to a random player, visible to everyone. The blip will follow the player around as they move. This could be used for manhunt, to emphasise a random player.

``` lua
-- Pick a random player
function setupRandomRobber ()
    local myPlayer = getRandomPlayer ()
    -- Create a radar blip at the player's position, with a 'cash' icon and only visible to everyone (no 'visibleTo' parameter)
    local myBlip = createBlipAttachedTo ( myPlayer, 52 )
end
```

</section>
See Also
--------
