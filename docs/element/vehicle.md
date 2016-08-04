The vehicle class represents vehicles in the GTA world. Vehicles can be occupied and controlled by players.

The element type of this class is **“vehicle”**.

XML syntax
----------

``` xml
<vehicle model="" posX="" posY="" posZ="" rotX="" rotY="" rotZ="" color="" upgrades="" paintjob="" plate="" turretX="" turretY="" health="" sirens="" landingGearDown="" specialState="" locked="" interior="" dimension="" frozen=""/>
```

### Required Attributes

-   **model**: The [vehicle ID](/docs/vehicle_ids.md "wikilink") of the vehicle being created.
-   **posX**: A float representing the X position of the vehicle.
-   **posY**: A float representing the Y position of the vehicle.
-   **posZ**: A float representing the Z position of the vehicle.

### Optional Attributes

-   **rotX**: A float representing the X rotation of the vehicle.
-   **rotY**: A float representing the Y rotation of the vehicle.
-   **rotZ**: A float representing the Z rotation of the vehicle.
-   **color**: An integer indicating the vehicle's [color(s)](/docs/vehicle_colors.md "wikilink") (seperated by commas).
-   **upgrades**: An integer representing the vehicle's mod upgrade(s) (seperated by commas), defined in San Andreas\\data\\maps\\veh\_mods\\veh\_mods.ide
-   **paintjob**: An integer indicating the vehicle's paint job (only works on certain vehicles).
-   **plate**: A set of up to 8 characters that will be shown on the vehicle's license plate.
-   **turretX**: the vehicle's turret's rotation around the Z axis, in radians. Relative to the vehicle's rotation, i.e. turretX=0 will always make the turret point in the same direction as the vehicle.
-   **turretY**: the vehicle's turret's rotation around the X axis, in radians. 0 means horizontal, positive values will make it point up and negative values point it down.
-   **health**: the vehicle's health. A value of 1000 means completely healthy, although higher values are allowed.
-   **sirens**: whether or not the vehicle's sirens are on (e.g. police cars and ambulances). Possible values are “true” and “false”.
-   **landingGearDown**: whether or not the vehicle's landing gear is down (only applicable to planes). Possible values are “true” and “false”.
-   **specialState**: the vehicle's adjustable property number.
-   **locked**: whether or not the vehicle's doors are locked. “true” or “false”.
-   **interior**: the interior number of the vehicle
-   **dimension**: the dimension number of the vehicle

Related scripting functions
---------------------------

[Category:Element Types](/docs/category-element_types.md "wikilink")

[it:Elemento/Veicolo](/docs/it-elemento/veicolo.md "wikilink")
