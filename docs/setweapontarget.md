This function sets the target of a [custom weapon](/docs/element/weapon.md "wikilink"). There are 3 different targeting modes, which are explained below.

Syntax (target an element)
--------------------------

Fires the weapon at a physical [element](/docs/element.md "wikilink").

``` lua
 )
```

### Required arguments

-   **theWeapon:** The weapon to set the target of.
-   **theTarget:** The [element](/docs/element.md "wikilink") to shoot at. It can be a [player](/docs/player.md "wikilink"), [ped](/docs/ped.md "wikilink"), [vehicle](/docs/vehicle.md "wikilink") or [object](/docs/object.md "wikilink").

### Optional arguments

-   **theComponent:** The component of the target to shoot at. This argument is only relevant when used in the following element types:
    -   **[Vehicles](/docs/vehicle.md "wikilink")**:
        -   **0**: front left tire.
        -   **1**: front right tire.
        -   **2**: rear left tire.
        -   **3**: rear right tire.
        -   **255**: center of the car (position returned by [getElementPosition](/docs/getelementposition.md "wikilink")).
    -   **[Peds](/docs/ped.md "wikilink")** (players **not** included; see [getPedBonePosition](/docs/getpedboneposition.md "wikilink") to know where is located each bone):
        -   **1:** *BONE\_PELVIS1* position.
        -   **2:** *BONE\_PELVIS* position.
        -   **3:** *BONE\_SPINE1* position.
        -   **4:** *BONE\_UPPERTORSO* position.
        -   **5:** *BONE\_NECK* position.
        -   **6:** *BONE\_HEAD2* position.
        -   **7:** *BONE\_HEAD1* position.
        -   **8:** *BONE\_HEAD* position.
        -   **21:** *BONE\_RIGHTUPPERTORSO* position.
        -   **22:** *BONE\_RIGHTSHOULDER* position.
        -   **23:** *BONE\_RIGHTELBOW* position.
        -   **24:** *BONE\_RIGHTWRIST* position.
        -   **25:** *BONE\_RIGHTHAND* position.
        -   **26:** *BONE\_RIGHTTHUMB* position.
        -   **31:** *BONE\_LEFTUPPERTORSO* position.
        -   **32:** *BONE\_LEFTSHOULDER* position.
        -   **33:** *BONE\_LEFTELBOW* position.
        -   **34:** *BONE\_LEFTWRIST* position.
        -   **35:** *BONE\_LEFTHAND* position.
        -   **36:** *BONE\_LEFTTHUMB* position.
        -   **41:** *BONE\_LEFTHIP* position.
        -   **42:** *BONE\_LEFTKNEE* position.
        -   **43:** *BONE\_LEFTANKLE* position.
        -   **44:** *BONE\_LEFTFOOT* position.
        -   **51:** *BONE\_RIGHTHIP* position.
        -   **52:** *BONE\_RIGHTKNEE* position.
        -   **53:** *BONE\_RIGHTANKLE* position.
        -   **54:** *BONE\_RIGHTFOOT* position.
        -   **255**: center of the ped (position returned by [getElementPosition](/docs/getelementposition.md "wikilink")).

### Returns

Returns *true* on success, *false* otherwise.

Syntax (target a position)
--------------------------

Fires the weapon at the specified position.

``` lua
bool setWeaponTarget ( weapon theWeapon, float targetX, float targetY, float targetZ )
```

### Required arguments

-   **theWeapon:** The weapon to set the target of.
-   **targetX:** The target X.
-   **targetY:** The target Y.
-   **targetZ:** The target Z.

### Returns

Returns *true* on success, *false* otherwise.

Syntax (rotational target)
--------------------------

Sets the weapon back to rotation based targeting. It will fire to its front.

``` lua
bool setWeaponTarget ( weapon theWeapon, nil )
```

### Required arguments

-   **theWeapon:** The weapon to clear the target of.

### Returns

Returns *true* on success, *false* otherwise.

Example
-------

This example creates a Uzi and a pedestrian in the center of the map when the resource which contains it starts and makes the weapon fire the new ped's head non-stop.

``` lua
local function createWeaponFiringPedHead()
    -- Create the weapon and set a flag of it
    local weapon = createWeapon("uzi", 0, 0, 10)
    setWeaponFlags(weapon, "instant_reload", true)
    -- Set the weapon target to a ped and fire it forever
    setWeaponTarget(weapon, createPed(8, 0, 0, 5), 8)
    setWeaponState(weapon, "firing")
end
addEventHandler("onClientResourceStart", resourceRoot, createWeaponFiringPedHead)
```

Requirements
------------

See also
--------
