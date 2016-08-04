This function is used to return an attribute of a node in a configuration file.

Syntax
------

``` lua
string xmlNodeGetAttribute ( xmlnode node, string name )             
```

### Required Arguments

-   **node:** The node from which you wish to return the attribute
-   **name:** The name of the attribute.

### Returns

Returns the attribute in string form or *false*, if the attribute is not defined.

Example
-------

Suppose we have a gametype where only one type of car is used, and this type should not depend on the map but rather be set in an external configuration file and be used in all maps. Here's an example where the configuration file is an XML document:

settings.xml

``` xml
<car model="528" posX="123.4" posY="456.7" posZ="12.3" rot="90.0" />
```

Lua code

``` lua
local xml = getResourceConfig("settings.xml")      -- load XML file and get its root element
local carmodel = xmlNodeGetAttribute(xml, "model")    -- get attribute of root element
local carX = xmlNodeGetAttribute(xml, "posX")
local carY = xmlNodeGetAttribute(xml, "posY")
local carZ = xmlNodeGetAttribute(xml, "posZ")
local carA = xmlNodeGetAttribute(xml, "rot")
createVehicle(carmodel, tonumber(carX), tonumber(carY), tonumber(carZ), 0.0, 0.0, tonumber(carA))
```

See Also
--------

[ru:xmlNodeGetAttribute](/ru:xmlNodeGetAttribute.md "wikilink")
