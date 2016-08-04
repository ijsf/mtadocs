This function can change an [element](/docs/element.md "wikilink")'s [visibility](/visibility.md "wikilink"). This does not work with all entities - [vehicles](/vehicle.md "wikilink"), [players](/player.md "wikilink") and [objects](/object.md "wikilink") are exempt. This is because these objects are required for accurate sync (they're physical objects that contribute to the physics engine). This function is particularly useful for changing the visibility of markers, radar blips and radar areas.

Visibility settings of lower elements in the element tree override higher ones - if visibility for root is set to false and for a player is set to true, it will be visible to the player.

If you want to clear all visibility settings of an object, try [clearElementVisibleTo](/docs/clearElementVisibleTo.md "wikilink")

Syntax
------

``` lua
bool setElementVisibleTo ( element theElement, element visibleTo, bool visible )
```

### Required Arguments

-   **theElement:** The element you want to control the visibility of.
-   **visibleTo:** The element you wish the element to be visible or invisible to. Any child elements that are players will also be able to see the element. See [visibility](/docs/visibility.md "wikilink").
-   **visible:** Whether you are making it visible or invisible to the player.

### Returns

Returns *true* if the element's visibility was changed successfully, *false* otherwise, for example if you are trying to change the visibility of a vehicle, player or object.

Example
-------

This example creates a marker and makes it only visibile to the player called 'someguy'.

``` lua
-- Find the player called someguy
local someguy = getPlayerFromName ( "someguy" )
-- If the player was found then
if ( someguy ) then
    -- Get the player's position into the variables x, y and z
    x, y, z = getElementPosition ( someguy )
    -- Create a marker at the player's position
    myMarker = createMarker ( x, y, z )
    -- Set marker visibility to true for someguy
    setElementVisibleTo ( myMarker, someguy, true )
    -- Then make the marker invisible to the whole dimension
    setElementVisibleTo ( myMarker, root, false )
    
    -- The order in which you do the visibility changes does not matter, but ideally trues should be set before falses in order to prevent a momentary flicker.
end
```

The following example shows how to make the marker visible to everyone except anotherguy

``` lua
-- Find the player called someguy
local someguy = getPlayerFromName ( "someguy" )
local anotherguy = getPlayerFromName ( "anotherguy" )
-- If the player was found then
if ( someguy ) then
    -- Get the player's position into the variables x, y and z
    x, y, z = getElementPosition ( someguy )
    -- Create a marker at the player's position
    myMarker = createMarker ( x, y, z )
    attachElements(myMarker, someguy)

    -- First make sure everyone is able to see the marker, this line is unnecessary in this case as root visibility is set to true by default behaviour
    setElementVisibleTo ( myMarker, root, true )

    -- Then hide it from anotherguy
    setElementVisibleTo ( myMarker, anotherguy, false )
end
```

See Also
--------
