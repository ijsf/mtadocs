This function provides an alternative way to load XML files to [getResourceConfig](/docs/getresourceconfig.md "wikilink"). This function loads an XML file and returns the node by specifying a specific file path, while [getResourceConfig](/docs/getresourceconfig.md "wikilink") allows for loading an XML file from a resource.

Syntax
------

``` lua
xmlnode xmlLoadFile ( string filePath )
```

### Required Arguments

-   **filePath:** The [filepath](/docs/filepath.md "wikilink") of the file in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the file is in, and 'path' is the path from the root directory of the resource to the file.

  
For example, if there is a file named 'settings.xml' in the resource 'ctf', it can be accessed from another resource this way: *xmlLoadFile(":ctf/settings.xml")*.

If the file is in the current resource, only the file path is necessary, e.g. *xmlLoadFile(“settings.xml”)*.

### Returns

Returns the root [xmlnode](/docs/xmlnode.md "wikilink") object of an xml file if successful, or *false* otherwise.

Example
-------

This example loads an XML file called *settings.xml* that is in a resource called *ctv*.

``` lua
node = xmlLoadFile ( ":ctv/settings.xml" )
```

See Also
--------

[ru:xmlLoadFile](/docs/ru:xmlloadfile.md "wikilink")
