This function is used to force a ped to use a gun.

Syntax
------

``` lua
bool makePedUseGun ( ped thePed, int useType, element target )
```

### Required Arguments

-   **thePed:** The [ped](/ped.md "wikilink") you wish to force the use of a gun upon.
-   **useType:** How the weapon should be used, will accept the following values:
    -   **0:** Do nothing
    -   **1:** Aim weapon
    -   **2:** Fire
    -   **3:** Burst-fire
    -   **4:** Reload
    -   **5:** Pistolwhip (Weapon melee)
    -   **6:** Cancel use
    -   **7:** Cancel use immediately
-   **target:** An [element](/element.md "wikilink") referring to the target that the ped will use its weapon against.

### Returns

Returns *true* if the command was successful, false otherwise.

Example
-------

``` lua
--ToDo
```

See Also
--------
