This function restores the visual DFF model of the given model ID. This restores the result of [engineReplaceModel](/docs/enginereplacemodel.md "wikilink").

Syntax
------

``` lua
bool engineRestoreModel ( int modelID )
```

### Required Arguments

-   **modelID:** The model ID to restore the visuals of

### Returns

Returns *true* if the model was successfully restored, *false* or *nil* if it failed for some reason.

Example
-------

<section name="Client" class="client" show="true">
Client-Side example for restoring model / vehicle.

``` lua
function ResetModel ( )
    engineRestoreModel ( 587 )  -- Object / Vehicle to restore to default GTA one.
end

addEvent ( "restoreClientModel", true )
addEventHandler ( "restoreClientModel", root, ResetModel )
```

</section>
<section name="Server" class="server" show="true">
Server-Side example for triggering model / vehicle restore function with “restore” command.

``` lua
function RestoreModel ( )
    triggerClientEvent ( "restoreClientModel", root, restoreClientModel )
end
addCommandHandler( "restore", RestoreModel )
```

</section>
See Also
--------
