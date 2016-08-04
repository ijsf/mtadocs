The interiors resource provides a generic system for use of the single player's interiors system, which is included in the MTASA 1.0 server package onwards. This means placing warp points where when players hit the marker, they are set into the appropriate interior.

Loading interiors from the resource
===================================

By default, the interiors resource offers over 200 of single player's own interior locations. Coupled with [dimensions](/docs/dimension.md "wikilink"), each and every warp point offers a unique location - with a total of over 450 locations.

Loading these interiors is easy. Starting the *interiors* resource will auto load all these preset warp points and will be ready to use out of the box.

Adding your own interiors
=========================

The interiors resource supports a flexible .map based element system to add your own interiors. The syntax follows an *entry* and *return* system. An *interiorEntry* element must have a unique id, and the *interiorReturn* element uses the “refid” attribute to link them together.

``` xml
<interiorEntry  id=""  posX=""  posY=""  posZ=""  rotation=""  dimension=""  interior="" oneway=""  />
<interiorReturn  refid=""  posX=""  posY=""  posZ=""  rotation=""  dimension=""  interior=""  />
```

Required Arguments
------------------

-   **posX**: A float representing the X position of the interior warp.
-   **posY**: A float representing the Y position of the interior warp.
-   **posZ**: A float representing the Z position of the interior warp.
-   **rotation**: A float representing the rotation of the player when he **reaches** the marker in the specified element.
-   **dimension**: An integer representing the dimension of the player when he **reaches** the interior warp in the specified element. In other words, which dimension the warp point exists.
-   **interior**: An integer representing the interior world of the player when he **reaches** the interior warp in the specified element. In other words, which interior the warp point exists.

Optional Arguments
------------------

-   **oneway**: If set to *true*, a interiorReturn marker will not be created, and the warp point will be one-way - from the interiorEntry to the interiorReturn with no way back.

Example
-------

``` xml
<interiorEntry  id="AMMUN1" posX="1368.35"  posY="-1279.06" posZ="12.55"    rotation="-0.100006"    dimension="0"   interior="0"    />
<interiorReturn refid="AMMUN1"  posX="286.15"   posY="-41.54"   posZ="1000.57"  rotation="90"   interior="1"    dimension="0"   />
```

The interiorEntry element here is located at 1368.35,-1279.06,12.55. When the player reaches this location, he will be warped to the attributes specified in the linked interiorReturn element - 286.15,-41.54,1000.57 with a rotation of 90 degrees, into the new interior world 1. When the player hits this marker again, the transverse will happen.

Interfacing your script with the interiors resource
===================================================

The interiors resource offers a few events and functions which should allow customisability of interiors.

Exported functions
------------------

Please remember that [call](/docs/call.md "wikilink") must be used to call functions of another resource.

------------------------------------------------------------------------

### getInteriorName

This function retrieves the overall name of an interior. This means it is the id or the overall refid.

#### Syntax

``` lua
string getInteriorName ( element interiorEntry/InteriorReturn )
```

#### Required Arguments

-   **interior:** The interior you wish to get the name of. Can be of type *interiorEntry* or *interiorReturn*.

#### Returns

Returns a string of the interior name, or false if it could not be retrieved.

------------------------------------------------------------------------

### getInteriorMarker

This function retrieves the [marker](/docs/marker.md "wikilink") element associated to the interior. This will allow you to modify the visibility of interior markers using the [setElementVisibleTo](/setElementVisibleTo.md "wikilink") function.

#### Syntax

``` lua
marker getInteriorMarker ( element interiorEntry/InteriorReturn )
```

#### Required Arguments

-   **interior:** The interior you wish to retrieve the associated marker of. Can be of type *interiorEntry* or *interiorReturn*.

#### Returns

Returns a marker element associated to the specified interior, or false if it could not be retrieved.

Events
------

### onInteriorHit

This event is triggered when an interior warp point is hit, prior to when a player is warped to his/her destination.

#### Parameters

``` lua
player hitPlayer
```

-   **hitPlayer**: The player that hit the interior warp point.

#### Source

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the interior element which was hit.

#### Cancel effect

If this event is [canceled](/docs/Event_system#Canceling.md "wikilink"), the player will not be warped to his destination point.

------------------------------------------------------------------------

### onInteriorWarped

This event is triggered when an interior destination has successfully been warped to.

#### Parameters

``` lua
player warpedPlayer
```

-   **warpedPlayer**: The player that has warped to the destination interior.

#### Source

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the interior element which was warped **to**.

------------------------------------------------------------------------

### onPlayerInteriorHit

This event is triggered when a player hits an interior warp point, prior to him reaching his destination

#### Parameters

``` lua
element hitInterior
```

-   **hitInterior**: The interior element that was hit.

#### Source

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the player who hit the interior element.

#### Cancel effect

If this event is [canceled](/docs/Event_system#Canceling.md "wikilink"), the player will not be warped to his destination point.

------------------------------------------------------------------------

### onPlayerInteriorWarped

This event is triggered when a player successfully warps to his destination interior.

#### Parameters

``` lua
element warpedInterior
```

-   **warpedInterior**: The interior that has been warped **to**.

#### Source

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the player who was warped to his destination point.

------------------------------------------------------------------------

### Examples

**Coming soon** [ru:<Resource:Interiors>](/docs/ru:Resource:Interiors.md "wikilink")
