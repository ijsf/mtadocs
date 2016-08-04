This function retrieves a resource's root element. The resource's root element is the element in the element tree which is the parent of all elements that belong to a particular resource (except for elements specifically created elsewhere). You can attach event handlers to this element to easily capture events that originate from your resource (and global events that originate from the root element).

Note: every resource has a [predefined global variable](/Predefined_variables_list.md "wikilink") called *resourceRoot* whose value is the root element of that resource.

Syntax
------

``` lua
element getResourceRootElement ( [resource theResource=getThisResource()] )
```

### Optional Arguments

-   **theResource:** the resource whose root element we are getting. If not specified, assumes the current resource. (the resource returned from [getThisResource](/getThisResource.md "wikilink"))

### Returns

Returns an *element* representing the resource's root, *false* if the specified resource doesn't exist.

Example
-------

<section name="Server" class="server" show="true">
This example retrieves the current resource's root element and attaches it to an onResourceStart event handler. This causes the event handler to get called only when the *current* resource is started rather than when *any* resource is started, thereby reducing unnecessary overhead.

``` lua
-- get the root element of this resource (the resource that the script is a part of)
resourceRoot = getResourceRootElement()

-- create a function to handle the onResourceStart event
function onCurrentResourceStart(theResource)
    local resourceName = getResourceName(theResource)
    outputChatBox("Hello and welcome to " .. resourceName .. "!")
end

-- add the event handler
addEventHandler("onResourceStart", resourceRoot, onCurrentResourceStart)
```

</section>
See Also
--------
