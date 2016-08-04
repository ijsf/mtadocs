This function creates a pickup element, which is placed in the GTA world and can be picked up to retrieve a health, armour or a weapon.

Syntax
------

``` lua
pickup createPickup ( float x, float y, float z, int theType, int amount/weapon/model, [ int respawnTime = 30000, int ammo = 50 ] )         
```

### Required Arguments

-   **x**: A floating point number representing the X coordinate on the map.
-   **y**: A floating point number representing the Y coordinate on the map.
-   **z**: A floating point number representing the Z coordinate on the map.
-   **theType**: This is an integer representing the type of pickup, representing the following types:
    -   **0**: Health Pickup
    -   **1**: Armour Pickup
    -   **2**: Weapon Pickup
    -   **3**: Custom Pickup

<!-- -->

-   **amount**: This is an integer representing the amount of Health points or Armour points a pickup has.

**OR**

-   **weapon**: If the type is a Weapon pickup, then it represents the [weapon ID](/Weapon.md "wikilink") of the weapon pickup. When used with the weapon pickup type set, the ammo parameter can be used.

**OR**

-   **model**: If the pickup is a custom model, this is the model id to use. Many non-pickup models can be used, though some may cause crashes. The following is a list of models designed to be used as pickups.
    -   **1212:** Money (Wad of Cash)
    -   **1240:** Health (heart)
    -   **1242:** Armour
    -   **1239:** Info icon
    -   **1272:** House (blue)
    -   **1273:** House (green)
    -   **1274:** Money (dollar symbol)
    -   **1241:** Adrenaline
    -   **1247:** Bribe
    -   **1248:** GTA III sign
    -   **1252:** Bomb from GTA III
    -   **1253:** Photo op
    -   **1254:** Skull
    -   **1274:** Money icon
    -   **1275:** Blue t-shirt
    -   **1277:** Save disk
    -   **1313:** 2 Skulls
    -   **1276:** Tiki statue
    -   **1310:** Parachute (with leg straps)
    -   **1318:** Down arrow
    -   **1279:** Drug bundle

**OR** Other ID Object

### Optional Arguments

-   **respawnTime**: How long before the pickup respawns in milliseconds (**This parameter is ignored on the client!**)
-   **ammo**: An integer representing the amount of ammo a pickup contains. This is only valid when the pickup type is a weapon pickup.

### Returns

Returns [pickup](/pickup.md "wikilink") [element](/element.md "wikilink") if the pickup was created succesfully, otherwise returns *false*.

Example
-------

<section name="Server" class="server" show="true">
This example creates a pickup after a player dies so that he drops his weapon.

``` lua
function createDeathPickup ( totalammo, killer, killerweapon, bodypart ) --when a player dies
    x, y, z = getElementPosition ( source ) --get the position of the person who died and define it as x, y and z
    currentweapon = getPlayerWeapon ( source ) --get the current weapon of the dead person
    createPickup ( x, y, z, 2, currentweapon, 10000, totalammo )
end
addEventHandler ( "onPlayerWasted", getRootElement(), createDeathPickup ) --add an event handler for onPlayerWasted
```

</section>
<section name="Server" class="server" show="false">
This example creates a custom pickup(money) after a player dies and sets it's value.

``` lua
function createDeathPickup ( totalammo, killer, killerweapon, bodypart ) --when a player dies
    x, y, z = getElementPosition ( source ) --get the position of the person who died and define it as x, y and z
    local money=createPickup ( x, y, z, 3, 1212, 10000)
    local playermoney = getPlayerMoney(source) --get the amount of money the dead person has
    setElementData(money,"Amount",playermoney) --now let's set the value of the pickup
    takePlayerMoney(source,playermoney) --Let's take away all their money
end
addEventHandler ( "onPlayerWasted", getRootElement(), createDeathPickup ) --add an event handler for onPlayerWasted
```

</section>
See Also
--------
