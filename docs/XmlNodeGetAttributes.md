Returns all the attributes of a specific XML node.

Syntax
------

``` lua
table xmlNodeGetAttributes ( xmlnode node )
```

### Required Arguments

-   **node:** the XML node to get the attributes of.

### Returns

If successful, returns a table with as keys the names of the attributes and as values the corresponding attribute values. If the node has no attributes, returns an empty table. In case of failure, returns *false*.

Example
-------

<section name="Server" class="server" show="true">
This example code opens the meta.xml of the resource it belongs to, and prints all attributes of the <info> node to the console.

``` lua
local meta = xmlLoadFile ( "meta.xml" )
local info = xmlFindChild ( meta, "info", 0 )
if info then
    local attrs = xmlNodeGetAttributes ( info )
    for name,value in pairs ( attrs ) do
        outputConsole ( name .. " = " .. value )
    end
end
xmlUnloadFile ( meta )
```

If the meta.xml looked like this:

``` xml
<meta>
    <info type="gamemode" name="My gamemode" author="me"/>
    ...
</meta>
```

Then the above code would output (not necessarily in this order):

``` lua
type = gamemode
name = My gamemode
author = me
```

</section>
See Also
--------

[ru:xmlNodeGetAttributes](/ru:xmlNodeGetAttributes.md "wikilink")
