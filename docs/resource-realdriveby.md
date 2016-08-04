Introduction
------------

RealDriveby is a fully customisable resource which allows a flexible driveby system for your server.

All of GTA's driveby compatible weapons, including the shotguns,pistols,M4 and AK-47 are supported by this resource. Shot delays for weapons such as pistols are fixed to their normal rate.

Users can switch weapons by default using the "Vehicle Look Left" and "Vehicle Look Right" keys while in driveby mode.

However, it is completely up to the admin how he or she wants drivebys to be: Using MTA's settings system, shot delays for weapons can be modified; the weapons which a driver can driveby with are customisable; the weapons a passenger can driveby with are customisable.

There are also options available to disable steering whilst in driveby mode, or disable drivebys altogether for certain vehicles.

On top of this, RealDriveby provides clientside scripting functions so that users can modify these attributes on a player-basis, allowing different players the ability to driveby different weapons and different delays.

Settings
--------

All settings can be modified using MTA's set() functions, modifying the meta.xml of the resource, or modifying the settings.xml.

### Driver weapons

-   **Setting name:** *driveby\_driver*
-   **Description:** Sets the weapons that a driver can driveby with. To disable driver drivebys, just pass an empty table. See [here](/docs/resource:realdriveby#gta_driveby_compatible_weapons.md "wikilink") for compatible weapons.
-   **XML Example:**
    ``` xml
    "/>
    ```

### Passenger weapons

-   **Setting name:** *driveby\_passenger*
-   **Description:** Sets the weapons that a passenger can driveby with. To disable passenger drivebys, just pass an empty table. See [here](/docs/resource:realdriveby#gta_driveby_compatible_weapons.md "wikilink") for compatible weapons.
-   **XML Example:**
    ``` xml
    "/>
    ```

### Shot delay

-   **Setting name:** *driveby\_shot\_delay*
-   **Description:** Sets the delay between each individual shot for the specified weapons. Unspecified weapons have GTA's default driveby fire rate. The setting is in the format of a table where the key is a **string** of the weapon ID, and the value is the delay in milliseconds.
-   **XML Example:**
    ``` xml
    "/>
    ```

### Blocked vehicles

-   **Setting name:** *driveby\_blocked\_vehicles*
-   **Description:** Sets the vehicles which driveby mode cannot be accessed in. Useful to block strange effects such as drivebys in tanks. In the format of an array of vehicle IDs.
-   **XML Example:**
    ``` xml
    "/>
    ```

### Steer Cars while in driveby mode

-   **Setting name:** *driveby\_steer\_cars*
-   **Description:** Sets whether drivers can steer left or right while in driveby mode for vehicles besides bikes. The setting is in the format of a bool, where *true* allows steering.
-   **XML Example:**
    ``` xml
    "/>
    ```

### Steer Bikes while in driveby mode

-   **Setting name:** *driveby\_steer\_bikes*
-   **Description:** Sets whether drivers can steer left or right while in driveby mode for bikes/bicycles. If set to false, it allows extra realism. The setting is in the format of a bool, where *true* allows steering.
-   **XML Example:**
    ``` xml
    "/>
    ```

### Auto-equip driveby weapon

-   **Setting name:** *driveby\_auto\_equip*
-   **Description:** Sets whether driveby mode will be enabled automatically when a player enters a vehicle.
-   **XML Example:**
    ``` xml
    "/>
    ```

### Toggle driveby mode key

-   **Setting name:** *driveby\_toggle\_mode*
-   **Description:** Sets the [key](/docs/key_names.md "wikilink") which will be used to toggle driveby mode.
-   **XML Example:**
    ``` xml
    <setting name="driveby_toggle_mode" value="mouse2"/>
    ```

### Next driveby weapon key

-   **Setting name:** *driveby\_next\_weapon*
-   **Description:** Sets the [key](/docs/key_names.md "wikilink") which will be used to change to the next driveby weapon (if there is one).
-   **XML Example:**
    ``` xml
    <setting name="driveby_next_weapon" value="vehicle_look_right"/>
    ```

### Previous driveby weapon key

-   **Setting name:** *driveby\_prev\_weapon*
-   **Description:** Sets the [key](/docs/key_names.md "wikilink") which will be used to change to the previous driveby weapon (if there is one).
-   **XML Example:**
    ``` xml
    <setting name="driveby_prev_weapon" value="vehicle_look_left"/>
    ```

Scripting functions
-------------------

All scripting functions are **clientside** and therefore only affect the **local player**. All functions must be called using the [call](/docs/call.md "wikilink") function, e.g.

``` lua
call(getResourceFromName("realdriveby"),"setWeaponShotDelay",22,300)
```

### setDriverDrivebyAbility

This function allows you to set what weapons the local player can use while a driver of a vehicle.

``` lua
bool setDriverDrivebyAbility ( table weapons )
```

-   **weapons:** An an array/table containing weapon IDs that the driver may use. See [here](/docs/resource:realdriveby#gta_driveby_compatible_weapons.md "wikilink") for compatible weapons.

### getDriverDrivebyAbility

This function allows you to retrive what weapons the local player can use while a driver of a vehicle.

``` lua
table getDriverDrivebyAbility ()
```

Returns a table of the weapons that can be used as a driver.

### setPassengerDrivebyAbility

This function allows you to set what weapons the local player can use while a passenger of a vehicle.

``` lua
bool setPassengerDrivebyAbility ( table weapons )
```

-   **weapons:** An an array/table containing weapon IDs that the passenger may use. See [here](/docs/resource:realdriveby#gta_driveby_compatible_weapons.md "wikilink") for compatible weapons.

### getPassengerDrivebyAbility

This function allows you to retrive what weapons the local player can use while a passenger of a vehicle.

``` lua
table getPassengerDrivebyAbility ()
```

Returns a table of the weapons that can be used as a passenger.

### setWeaponShotDelay

This function allows setting of a certain weapon's shot delay for the local player

``` lua
bool setWeaponShotDelay(int weaponID, int delay)
```

-   **weaponID:** An integer representing the [weapon ID](/docs/weapons.md "wikilink") of the delay that you wish to set.
-   **delay:** An integer representing the delay in between each shot, in **milliseconds**.

### getWeaponShotDelay

This function allows retrieving of a certain weapon's shot delay for the local player

``` lua
int getWeaponShotDelay(int weaponID)
```

-   **weaponID:** An integer representing the [weapon ID](/docs/weapons.md "wikilink") of the delay that you wish to retrieve.

Returns an integer representing the weapon delay in between each shot.

### setDrivebySteeringAbility

This function allows setting of whether the local player can steer while in driveby mode.

``` lua
bool setDrivebySteeringAbility( bool otherVehicles, bool bikes )
```

-   **otherVehicles:** A bool representing whether steering is enabled while in any vehicle besides a bike/bicycle, where *true* represents enabled steering and *false* represents disabled steering.
-   **bikes :** A bool representing whether steering is enabled while in a bike/bicycle, where *true* represents enabled steering and *false* represents disabled steering.

### getDrivebySteeringAbility

This function allows retrieving of whether the local player can steer while in driveby mode.

``` lua
bool getDrivebySteeringAbility( string drivebyType )
```

-   **drivebyType :** A string which can either be "**bike**", representing bikes/bicycles, or "**car**" representing all other vehicles.

Returns a bool of the ability of the specified type of driveby, where *true* is enabled and *false* is disabled.

### setDrivebyAutoEquip

This function allows setting of whether driveby mode is enabled automatically upon entering a vehicle, for the local player.

``` lua
bool setDrivebyAutoEquip( bool enabled )
```

-   **enabled :** A bool whether auto-equip should be enabled

### getDrivebyAutoEquip

This function allows retrieving of whether driveby mode is enabled automatically upon entering a vehicle, for the local player.

``` lua
bool getDrivebyAutoEquip()
```

Returns a bool of whether auto-equipping is enabled.

GTA Driveby Compatible weapons
------------------------------

These are weapons that are compatible with GTA/MTA's driveby mode, and can be used by this script.

<table border="1" class="unnamed1">
<tr>
<th>
Name

</th>
<th>
ID

</th>
<td>
</td>
<th>
Name

</th>
<th>
ID

</th>
</tr>
<tr>
<td>
Pistol

</td>
<td>
22

</td>
<td>
</td>
<td>
Silenced Pistol

</td>
<td>
23

</td>
</tr>
<tr>
<td>
Desert Eagle

</td>
<td>
24

</td>
<td>
</td>
<td>
Chrome Shotgun

</td>
<td>
25

</td>
</tr>
<tr>
<td>
Sawn-Off Shotgun

</td>
<td>
26

</td>
<td>
</td>
<td>
Combat Shotgun

</td>
<td>
27

</td>
</tr>
<tr>
<td>
Uzi

</td>
<td>
28

</td>
<td>
</td>
<td>
MP5

</td>
<td>
29

</td>
</tr>
<tr>
<td>
Tec-9

</td>
<td>
32

</td>
<td>
</td>
<td>
AK-47

</td>
<td>
30

</td>
</tr>
<tr>
<td>
M4

</td>
<td>
31

</td>
<td>
</td>
<td>
Country Rifle

</td>
<td>
33

</td>
</tr>
<tr>
<td>
Minigun

</td>
<td>
38

</td>
<td>
</td>
<td>
</td>
<td>
</td>
</tr>
</table>
[ru:<Resource:Realdriveby>](/docs/ru:resource:realdriveby.md "wikilink")
