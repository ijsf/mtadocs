This function retrieves the reason why a resource failed to start.

Syntax
------

``` lua
string getResourceLoadFailureReason ( resource theResource )
```

### Required Arguments

-   **theResource:** The resource you wish to check.

### Returns

If the resource failed to load, returns a string with the failure reason in it. If it loaded successfully, returns an empty string. Returns *false* if the resource doesn't exist.

Example
-------

<section name="Server" class="server" show="true">
This example checks if there's a resource that failed to load, then outputs “Resource: 'resourceName' failed to load because 'reason'.” .

``` lua
for _,v in ipairs(getResources())do --loop through all the resources
    if getResourceState(v)=="failed to load" then --check if it failed to load
        outputChatBox("Resource: "..getResourceName(v).." failed to load because: "..getResourceLoadFailureReason(v)..".") --output why it didn't load
    end
end
```

</section>
See Also
--------
