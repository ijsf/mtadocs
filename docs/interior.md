An *interior* in GTA is an area that isn't 'outside'. For example, inside houses, casinos, restaurants, shops etc. Players can not, by default, access these. You can use various scripting functions to move elements into these interiors. When you change the interior a player is in, they can only see the non-player elements in that interior. Players can see each other in whatever interior they are in.

You can have up to 255 interiors, interior 0 being the first one and referring to the normal GTA world.

Uses
----

To allow a player to enter an interior, you should use the [setElementInterior](/docs/setelementinterior.md "wikilink") function on the player you wish to move. You can also use this function on other elements, for example to make a vehicle or object appear in the interior.

Dimensions
----------

The original GTA interiors are reused in a number of places throughout the game - e.g. each fast food restaurant interior is used many times. [Dimensions](/docs/dimension.md "wikilink") are a feature that was added to MTA to solve this problem. You can allocate each instance of the interior a separate dimension which will mean that the players in each dimension won't be able to see each other or interact with each other. This will mean that the interiors appear to be entirely separate, despite physically being in the same place.

Relevant scripting functions
----------------------------

-   [getElementInterior](/docs/getelementinterior.md "wikilink")
-   [setElementInterior](/docs/setelementinterior.md "wikilink")
-   [spawnPlayer](/docs/spawnplayer.md "wikilink")

See Also
--------

-   [List of interior IDs](/docs/interior_ids.md "wikilink")
-   [Dimension](/docs/dimension.md "wikilink")

[de:Interior](/docs/de:interior.md "wikilink") [Category:Scripting Concepts](/docs/category:scripting_concepts.md "wikilink")
