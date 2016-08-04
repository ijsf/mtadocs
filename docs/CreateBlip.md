This function creates a [blip](/docs/blip.md "wikilink") [element](/element.md "wikilink"), which is displayed as an icon on the client's radar.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
blip createBlip ( float x, float y, float z [, int icon = 0, int size = 2, int r = 255, int g = 0, int b = 0, int a = 255, int ordering = 0, float visibleDistance = 99999.0, visibleTo = getRootElement( ) ] )
```

</section>
<section name="Client" class="client" show="true">
``` lua
blip createBlip ( float x, float y, float z [, int icon = 0, int size = 2, int r = 255, int g = 0, int b = 0, int a = 255, int ordering = 0, float visibleDistance = 99999.0 ] )
```

</section>
### Required Arguments

-   **x:** The x position of the blip, in world coordinates.
-   **y:** The y position of the blip, in world coordinates.
-   **z:** The z position of the blip, in world coordinates.

### Optional Arguments

-   **icon:** The icon that the radar blips should be. Valid values can be seen at [Blip Icons](/docs/Blip_Icons.md "wikilink")
-   **size:** The size of the radar blip. Only applicable to the *Marker* icon. Default is 2.
-   **r:** The amount of red in the blip's color (0 - 255). Only applicable to the *Marker* icon. Default is 255.
-   **g:** The amount of green in the blip's color (0 - 255). Only applicable to the *Marker* icon. Default is 0.
-   **b:** The amount of blue in the blip's color (0 - 255). Only applicable to the *Marker* icon. Default is 0.
-   **a:** The amount of alpha in the blip's color (0 - 255). Only applicable to the *Marker* icon. Default is 255.

<section name="Server" class="server" show="true">
-   **visibleTo:** This defines which elements can see the blip. Defaults to visible to everyone. See [visibility](/docs/visibility.md "wikilink").

</section>
Returns
-------

Returns an [element](/docs/element.md "wikilink") of the [blip](/blip.md "wikilink") if it was created successfully, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
**Example 1:** This example creates a radar blip at a random player's position and makes it so that it is only visible to that player.

``` lua
-- Pick a random player
local myPlayer = getRandomPlayer( )
-- Retrieve the player's position and store it in the variables x, y and z
local x, y, z = getElementPosition( myPlayer )
-- Create a radar blip at the player's position, with a 'cash' icon and only visible to the player
local myBlip = createBlip( x, y, z, 51, 0, 0, 0, 255, myPlayer )
```

**Example 2:** This example attaches a blip to a player. You can attach a blip to an element by just setting the blip's parent to that element.

``` lua
-- Pick a random player
local myPlayer = getRandomPlayer( )
-- Create a radar blip in the middle of the map
local myBlip = createBlip( 0, 0, 0 )
-- Make the player the parent of the blip, so that the blip follows the player around
setElementParent( myBlip, myPlayer )
```

</section>
See Also
--------

[AR:createBlip](/docs/AR:createBlip.md "wikilink") [es:createBlip](/es:createBlip.md "wikilink") [DE:createBlip](/DE:createBlip.md "wikilink")
