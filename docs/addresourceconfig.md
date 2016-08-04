This function adds a new empty config file to an existing resource.

Syntax
------

``` lua
xmlnode addResourceConfig ( string filePath, [ string filetype = "server" ] )
```

### Required Arguments

-   **filePath:** The [filepath](/docs/filepath.md "wikilink") of the file to be created in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the file is in, and 'path' is the path from the root directory of the resource to the file.

  
For example, if you want to create a config named 'settings.xml' in the resource 'ctf', it can be created from another resource this way: *addResourceConfig(":ctf/settings.xml", “server”)*.

If you want to create the file in the current resource, only the file path is necessary, e.g. *addResourceConfig(“settings.xml”, “server”)*.

### Optional Arguments

-   **filetype:** a string indicating whether the file is serverside (“server”) or clientside (“client”).

### Returns

Returns the new config's root [xmlnode](/docs/xmlnode.md "wikilink") if the config was added successfully, *false* otherwise.

Example
-------

<section name="Server Example" class="server" show="true">
``` lua
function onStart()
   addResourceConfig(":ctf/settings.xml", "server")
end
addEventHandler("onResourceStart",getResourceRootElement(),onStart)
```

</section>
See Also
--------
