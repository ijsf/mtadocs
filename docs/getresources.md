This function retrieves a table of all the resources that exist on the server.

Syntax
------

``` lua
table getResources ()
```

### Returns

Returns a table of resources.

Example
-------

This function lists all loaded resources in the console.

``` lua
function displayResources()
     outputConsole("List of resources:")
     local resourceTable = getResources() -- get a table of resources
     for resourceKey, resourceValue in ipairs(resourceTable) do
          -- iterate through the table and output each resource's name
          local name = getResourceName(resourceValue)
          outputConsole(" " .. name)
     end
end
```

See Also
--------
