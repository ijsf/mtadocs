This function checks whether an [element](/element.md "wikilink") is currently streamed in (not virtualized) and are actual GTA objects in the world. You can force an element to be streamed in using [setElementStreamable](/setElementStreamable.md "wikilink").

Syntax
------

``` lua
bool isElementStreamedIn ( element theElement )
```

### Required Arguments

-   **theElement**: The [element](/element.md "wikilink") to check whether is streamed in or not.

### Returns

Returns *true* if the passed element is currently streamed in, *false* if it is virtualized.

Example
-------

This command shows you how many objects you have streamed in.

``` lua
function checkTheObjects ( cmd )
    local amount = 0 -- When starting the command, we don't have any objects looped.
    for k,v in ipairs ( getElementsByType ( "object" ) ) do -- Looping all the objects in the server
        if isElementStreamedIn ( v ) then -- If the object is streamed in
            amount = amount + 1 -- It's an object more streamed in
        end
    end
    outputChatBox ( "You have currently " ..amount.. " objects streamed in." ) -- Send the player the amount of objects that are streamed in
end
addCommandHandler ( "checkobjects", checkTheObjects )
```

Note: Objects can already stream from a very long distance, so even when you can't see some objects, they can still be returned.

See Also
--------
