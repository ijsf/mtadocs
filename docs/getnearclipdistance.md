Syntax
------

``` lua
float getNearClipDistance ( )
```

### Returns

This function returns a *[float](/docs/float.md "wikilink")* containing the actual near clip distance.

Example
-------

This example adds a */testmynearclipdistance* command which outputs different things deppending of the current near clip distance.

    local function tellPlayerNearClipFacts()
        local nearClipDistance = getNearClipDistance()
        outputChatBox(nearClipDistance == 0.3 and "Your near clip distance is normal." or (nearClipDistance > 0.3 and "Be aware! You shouldn't be able to see very near objects so well!" or "You should be able to see very near objects so well!"))
    end
    addCommandHandler("testmynearclipdistance", tellPlayerNearClipFacts)

See also
--------
