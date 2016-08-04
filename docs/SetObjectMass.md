Syntax
------

``` lua
bool setObjectMass ( object theObject, float mass )
```

### Required Arguments

-   **theObject:** the object whose mass will be set.
-   **mass:** the new mass.

### Returns

-   *true* if the new mass value has been.
-   *false* otherwise.

Example
-------

This script basically creates an object then get's the mass and set's its mass 300 more than it's original mass, then tell the client the old and new mass of the object.

``` lua
local object = createObject(1225,0,0,3)
local oldMass = getObjectMass(object)
local newMass = oldMass+300.0
setObjectMass(object,newMass)
outputChatBox("Object Old Mass: "..oldMass..", New Mass: "..newMass)
```

See Also
--------
