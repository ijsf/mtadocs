This function is used to return the root node of a configuration file. Config files must be predefined in a resource's [meta file](/docs/meta.xml.md "wikilink"). An alternative way to load XML files is to use [xmlLoadFile](/docs/xmlloadfile.md "wikilink").

Syntax
------

``` lua
xmlnode getResourceConfig ( string filePath )
```

### Required Arguments

-   **filePath:** The [filepath](/docs/filepath.md "wikilink") of the file in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the file is in, and 'path' is the path from the root directory of the resource to the file.

  
For example, if there is a file named 'settings.xml' in the resource 'ctf', it can be accessed from another resource this way: *getResourceConfig(":ctf/settings.xml")*.

If the file is in the current resource, only the file path is necessary, e.g. *getResourceConfig(“settings.xml”)*.

### Returns

Returns the root node of the specified configuration file. If the file is corrupted, not defined in the meta file or doesn't exist, returns false.

Example
-------

<section name="Server" class="server" show="true">
This example opens a configuration file and prints the value of the 'attr' attribute of the first 'group' node.

``` lua
function resourceStart ( )                         -- When the resource is started
    local node = getResourceConfig( "config.xml" )  -- get the configuration file
    local subNode = xmlFindChild( node, "group", 0 )      -- get a subnode in it
    outputChatBox( xmlNodeGetAttribute( subNode, "attr" ),root )    -- output its attributes value to chatbox
end
addEventHandler ( "onResourceStart", resourceRoot, resourceStart )
```

</section>
See Also
--------
