This function creates a subnode for a specified XML node.

Syntax
------

``` lua
xmlnode xmlCreateSubNode ( xmlnode parentNode, string tagname )
```

### Required Arguments

-   **parentNode:** the [xmlnode](/xmlnode.md "wikilink") you want to create a subnode of.
-   **tagname:** the type of the subnode that will be created.

### Returns

Returns the created [xmlnode](/xmlnode.md "wikilink") if successful, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
We need to create a new node between the tags <config> and &lt;/ config&gt;. config.xml:

``` xml
<config>
    <newnode>somevalue</newnode>
</config>
```

Lua code:

``` lua
function()
    config = xmlLoadFile("config.xml")
    local newNode = xmlCreateSubNode ( config, "newnode" )
    xmlNodeSetValue ( newNode, "somevalue" )
    xmlSaveFile( config )
end
```

</section>
See Also
--------
