This function sets the value of any attribute in a resource info tag.

**Note:** that this is protected under [ACL](/docs/acl.md "wikilink") ModifyOtherObjects.

Syntax
------

``` lua
bool setResourceInfo ( resource theResource, string attribute, string value ) 
```

### Required Arguments

-   **theResource:** the resource we are setting info to.
-   **attribute:** the name of the attribute that is to be set.
-   **value:** the value of this attribute

### Returns

Returns *true* if the info was successfully set, *false* otherwise

Example
-------

This function sets the author of the current resource.

``` lua
function outputAuthor(newAuthorName)
    author = getResourceInfo ( getThisResource(), "author" )    --Get the authors name
    if author then    --if it exists
        outputChatBox( author .. " made this script." )    --tell the world his name
    else    --if it doesn't
        setResourceInfo ( getThisResource(), "author", newAuthorName )
        outputChatBox( "Author set to: "..newAuthorName )    --tell them that it was set
    end
end
```

See Also
--------
