This function restores the original collision model of the given model ID. Reverses the effect of [engineReplaceCOL](/docs/engineReplaceCOL.md "wikilink").

Syntax
------

``` lua
bool engineRestoreCOL ( int modelID )
```

### Required Arguments

-   **modelID:** The ID of the model to restore the model of

### Returns

Returns *true* if this function succeeds, *false* or *nil* if it fails for some reason.

Example
-------

<section name="Client" class="client" show="true">
Client-Side example for restoring object collision with default one.

``` lua
function RestoreCollision ( )
    engineRestoreCOL ( 3356 )
end

addEvent ( "collisionRestore", true )
addEventHandler ( "collisionRestore", getRootElement(), RestoreCollision )
```

</section>
<section name="Server" class="server" show="true">
Server-side example function for triggering the restore.

``` lua
function RestoreCols ( )
    triggerClientEvent ( "collisionRestore", getRootElement(), collisionRestore )
end
addCommandHandler("restorecol", RestoreCols)
```

</section>
See Also
--------
