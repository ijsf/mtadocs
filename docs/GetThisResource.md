This function retrieves the resource from which the function call was made.

Note: every resource has a predefined global variable called *resource* that contains the resource pointer for that resource, in other words, the value that this function returns.

Syntax
------

``` lua
resource getThisResource ( )
```

### Returns

Returns the resource in which the current script is.

Example
-------

This example retrieves the current resource's root element and attaches it to an onResourceStart event handler. This causes the event handler to get called only when the *current* resource is started rather than when *any* resource is started, thereby reducing unnecessary overhead.

``` lua
-- get the root element of this resource (the resource that the script is a part of)
resourceRoot = getResourceRootElement(getThisResource()) 
--getThisResource() is the same thing as MTA's secret global variable 
--"resource" as explained in the note above. 

-- create a function to handle the command
function onResourceCommand()
   local thisResource = getThisResource()
   local resourceName = getResourceName(thisResource)
   outputChatBox("You are in the " .. resourceName .. " resource!")
end

-- add the event handler
addCommandHandler("what", onResourceCommand)
```

See Also
--------
