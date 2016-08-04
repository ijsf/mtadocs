Sets the tag name of the specified XML node.

Syntax
------

``` lua
bool xmlNodeSetName ( xmlnode node, string name )
```

### Required Arguments

-   **node:** the node to change the tag name of.
-   **name:** the new tag name to set.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

``` lua
local xml = xmlCreateFile("fileName.xml","Test")
local xmlNode = xmlCreateChild(xml,"Test1")
local xmlNodeName = xmlNodeGetName(xmlNode)
if xmlNodeName == "Test1" then
   xmlNodeSetName(xmlNode, "Test2")
end
```

See Also
--------

[ru:xmlNodeSetName](/docs/ru:xmlnodesetname.md "wikilink")
