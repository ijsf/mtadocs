This function is used to change the handling data of all vehicles of a specified model.

Syntax
------

``` lua
bool setModelHandling ( int modelId, string property, var value ) 
```

### Required Arguments

-   **modelId:** The [vehicle model](/Vehicle_IDs.md "wikilink") you wish to set the handling of.
-   **property:** The property you wish to set the handling of the vehicle to, or *nil* if you want to reset the all the handling properties.
-   **value:** The value of the models's handling property you wish to set, or *nil* if you want to reset the handling property to its default value.

### Returns

Returns *true* if the handling was set successfully, *false* otherwise.

Handling Properties
-------------------

See below a list of valid properties and their required values:

Example
-------

<section name="Server" class="server" show="true">
This example script changes the handling of all Bullet.

``` lua
function handlingChange()
    setModelHandling(541, "mass", 1890)
    setModelHandling(541, "turnMass", 3780)
    setModelHandling(541, "dragCoeff", 0.7)
    setModelHandling(541, "centerOfMass", {0.0, 0.1, -0.2} )
    setModelHandling(541, "percentSubmerged", 75)
    setModelHandling(541, "tractionMultiplier", 0.70)
    setModelHandling(541, "tractionLoss", 0.90)
    setModelHandling(541, "tractionBias", 0.50)
    setModelHandling(541, "numberOfGears", 5)
    setModelHandling(541, "maxVelocity", 407)
    setModelHandling(541, "engineAcceleration", 50)
    setModelHandling(541, "engineInertia", 10)
    setModelHandling(541, "driveType", "awd")
    setModelHandling(541, "engineType", "petrol")
    setModelHandling(541, "brakeDeceleration", 11)
    setModelHandling(541, "brakeBias", 0.45)
    setModelHandling(541, "ABS", false)
    setModelHandling(541, "steeringLock", 30)
    setModelHandling(541, "suspensionForceLevel", 0.80)
    setModelHandling(541, "suspensionDamping", 0.20)
    setModelHandling(541, "suspensionHighSpeedDamping", 0.0)
    setModelHandling(541, "suspensionUpperLimit", 0.10)
    setModelHandling(541, "suspensionLowerLimit", -0.09)
    setModelHandling(541, "suspensionFrontRearBias", 0.5)
    setModelHandling(541, "suspensionAntiDiveMultiplier", 0.6)
    setModelHandling(541, "seatOffsetDistance", 0.3)
    setModelHandling(541, "collisionDamageMultiplier", 0.50)
    setModelHandling(541, "monetary", 1460000)
    setModelHandling(541, "modelFlags", 0xC0222004)
    setModelHandling(541, "handlingFlags", 0x1400000)
    setModelHandling(541, "headLight", 1)
    setModelHandling(541, "tailLight", 1)
    setModelHandling(541, "animGroup", 0)
end
addEventHandler("onResourceStart", resourceRoot, handlingChange)
```

This function will reset the handling of Bullet vehicles to its default state.

``` lua
function resetHandling()
    for k,_ in pairs(getModelHandling(541)) do
        setModelHandling(541, k, nil)
    end
end
addEventHandler("onResourceStop", resourceRoot, resetHandling)
```

</section>
Issues
------

See other vehicle functions
---------------------------
