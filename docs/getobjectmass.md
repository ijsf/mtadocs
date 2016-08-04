Syntax
------

``` lua
float getObjectMass ( object theObject )
```

### Required Arguments

-   **theObject:** the object whose mass you want to get.

### Returns

-   A [float](/docs/float.md "wikilink") representing the mass of the object.
-   *false* if invalid arguments were passed.
-   *-1* if object was never streamed in.

Example
-------

This script basically creates an object then get's the mass and set's its mass 300 more than it's original mass, then tell the client the old and new mass of the object.

``` lua
local object = createObject(1337,0,0,3)
local oldMass = getObjectMass(object)
local newMass = oldMass+300.0
setObjectMass(object,newMass)
outputChatBox("Object Old Mass: "..oldMass..", New Mass: "..newMass)
```

See Also
--------
