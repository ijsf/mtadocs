This function returns the state of a given resource

Syntax
------

``` lua
string getResourceState ( resource theResource ) 
```

### Required Arguments

-   **theResource:** The resource you wish to get the name of.

### Returns

If successful returns a string with the resource state in it, *false* otherwise. The state can be one of:

-   **loaded**
-   **running**

Example
-------

This example returns the state of a given resource. Syntax: */state <Resource Name>*

``` lua
function getState( player, command, resourceName )
    if resourceName then
        local resource = getResourceFromName( resourceName )
        if resource then
            outputChatBox( "Resource State: " .. resourceName .. " is currently " .. getResourceState( resource ) .. ".", player, 0, 0, 255 )
        else
            outputChatBox( "Error: No resource with name " .. resourceName .. " exists.", player, 255, 0, 0 )
        end
    else
        outputChatBox( "Syntax: " .. command .. " [resource name]", player, 255, 0, 0 )
    end
end

addCommandHandler( "state", getState )
```

See Also
--------
