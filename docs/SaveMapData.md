This converts a set of elements in the element tree into XML. This is a format that can then be loaded as a map file. Each element represents a single XML node.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **node**: An existing node that should contain the contents of baseElement
-   **baseElement**: The first element to output to the xml tree. This element and all its children (and their children, etc) will be output.

### Optional Arguments

-   **childrenOnly**: Defines if you want to only save children of the specified element.

### Returns

Example
-------

Saving your resource's data to an map file (untested)

``` lua
local file = xmlCreateFile("saved.map", "map")
if file then
   saveMapData ( file, getResourceRootElement(getThisResource()) )
   xmlSaveFile ( file )
   xmlUnloadFile ( file )
end
```

See Also
--------
