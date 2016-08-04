The pickup class represents weapon, health, or armor pickups in the GTA world. Pickups can be picked up by players when they are walked over. Players will not be given health or armor pickups if their health or armor is already full.

The element type of this class is **“pickup”**.

XML syntax
----------

``` xml
<pickup posX="" posY="" posZ="" type="" amount="" respawn=""/>
```

### Required Attributes

-   **posX**: A float representing the X position of the pickup.
-   **posY**: A float representing the Y position of the pickup.
-   **posZ**: A float representing the Z position of the pickup.
-   **type**: A string indicating the type of the pickup. This can either be “health”, “armor”, or an integer representing the [weapon ID](/docs/weapon.md "wikilink") of the pickup..

### Optional Attributes

-   **amount**: An integer representing a the amount in a pickup. For health or armor, this represents the number of hit points for the pickup. For weapons, this represents the amount of ammo
-   **respawn**: An integer representing the number of milliseconds until the pickup reappears after it has been picked up (default: 30000).

Related scripting functions
---------------------------

[Category:Element Types](/docs/category:element_types.md "wikilink")
