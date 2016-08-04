Gets the tag name of the specified XML node.

Syntax
------

``` lua
string xmlNodeGetName ( xmlnode node )
```

### Required Arguments

-   **node:** the node to get the tag name of.

### Returns

Returns the tag name of the node if successful, *false* otherwise.

<section name="Example 1" class="both" show="true">
Example
-------

``` lua
local xml = xmlCreateFile("test.xml","test")
local xmlNode = xmlCreateChild(xml,"nextTest")
local xmlNodeName = xmlNodeGetName(xmlNode)
outputConsole(xmlNodeName) --This should output "nextTest".
```

</section>
See Also
--------

[ru:xmlNodeGetName](/docs/ru-xmlnodegetname.md "wikilink")
