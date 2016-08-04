This function retrieves the *dynamic element root* of a specified [resource](/docs/resource.md "wikilink"). The *dynamic element root* is the parent of elements that are created by scripts (e.g. with [createObject](/docs/createobject.md "wikilink")) unless they specify a different parent.

Syntax
------

``` lua
element getResourceDynamicElementRoot ( resource theResource ) 
```

### Required Arguments

-   **theResource:** the resource of which dynamic element root we want.

### Returns

Returns an [element](/docs/element.md "wikilink") of the resource's dynamic element root if the resource specified was valid and active (currently running), *false* otherwise.

Example
-------

This example shows how to get all elements by specific type, created only by resource scripts (not maps).

``` lua
-- We have some map files with many objects in our meta.xml.
-- And we have some objects, created by some resource scripts.

--      createObject(...) -- 1
--      createObject(...) -- 2
--      ...
--      createObject(...) -- 20

-- After resource start we must found all objects, created only
-- by current resource scripts (not maps) and make them invisible.

-- `resourceRoot` is predefined script variable containing current resource root pointer
addEventHandler( 'onResourceStart', resourceRoot,
    function()
        -- `resource` is predefined script variable containing current resource pointer
        local thisResourceDynamicRoot = getResourceDynamicElementRoot(resource)
        local onlyScriptObjects = getElementsByType( 'object', thisResourceDynamicRoot )
        
        for scriptObject in ipairs(onlyScriptObjects) do
            setElementAlpha( scriptObject, 0 )
        end
    end
)
```

See Also
--------
