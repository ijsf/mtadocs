This function returns the root node of the [element tree](/element_tree.md "wikilink"), called *root*. This node contains every other element: all resource root elements, players and remote clients. It is never destroyed and cannot be destroyed using [destroyElement](/destroyElement.md "wikilink").

It is often used to attach handler functions to events triggered for any element, or also to make a scripting function affect all elements.

Syntax
------

``` lua
element getRootElement ( )
```

### Returns

Returns the root [element](/element.md "wikilink").

Example
-------

This example will output the number of loaded resources by counting *resource* elements that are children of the *root* node.

``` lua
--By default, predefined variable 'root' is getRootElement()
local rootChildren = getElementChildren( root )

local resourceCount = 0
for k, child in ipairs( rootChildren ) do
    if getElementType( child ) == "resource" then
        resourceCount = resourceCount + 1
    end
end

outputChatBox( "There are " .. resourceCount .. " loaded resources." )
```

See Also
--------

[ru:getRootElement](/ru:getRootElement.md "wikilink")
