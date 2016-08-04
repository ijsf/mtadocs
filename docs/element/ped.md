The word “ped” is short for “pedestrian” and describes any person in GTA, be it a player or an NPC character. (And even though “pedestrian” doesn't technically apply to people that drive, they still fall under this name)

The [createPed](/docs/createPed.md "wikilink") function specifically creates an NPC, but all other ped functions work on both players and NPC's as they're pretty much the same thing to San Andreas.

The element type of a NPC is **“ped”**.

XML syntax
----------

``` xml
<ped model="" posX="" posY="" posZ="" rotZ="" interior="" frozen="" />
```

### Required Attributes

-   **model**: The [character skin ID](/docs/Character_Skins.md "wikilink") of the ped being created.
-   **posX**: A float representing the X position of the ped.
-   **posY**: A float representing the Y position of the ped.
-   **posZ**: A float representing the Z position of the ped.

### Optional Attributes

-   **rotZ**: A float representing the Z rotation of the ped.
-   **interior**: A interior where the ped spawns.

Related scripting functions
---------------------------

[Category:Element Types](/docs/Category:Element_Types.md "wikilink")
