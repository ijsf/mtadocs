Used to check the last starting time and date of a resource

Syntax
------

### Required Arguments

-   **theResource:** The resource of which you'd like to check the last starting time.

### Returns

Example
-------

This function outputs to chatbox when the current resource was started.

``` lua
function whenStarted()
    local startTime = getResourceLastStartTime ( getThisResource() )    --Get the time and date
    outputChatBox( "This resource was started on: " .. startTime )    --tell everybody when the current resource was started.
end
```

See Also
--------
