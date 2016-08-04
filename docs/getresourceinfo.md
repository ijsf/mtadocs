This function retrieves the value of any attribute in a resource info tag.

Syntax
------

``` lua
string getResourceInfo ( resource theResource, string attribute ) 
```

### Required Arguments

-   **theResource:** the resource we are getting the info from.
-   **attribute:** the name of the attribute we want info about.

### Returns

Returns a *string* with the attribute value if it exists, *false* otherwise.

Example
-------

This function tells the server who's the author who made the currently running resource.

``` lua
function outputAuthor()
    author = getResourceInfo ( getThisResource(), "author" )    --Get the authors name
    if author then    --if it exists
        outputChatBox( author .. " made this script." )    --tell the world his name
    else    --if it doesn't
        outputChatBox( "I've no idea who made this script." )    --apologize.
    end
end
```

See Also
--------
