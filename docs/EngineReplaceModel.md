This function replaces the given model ID with the model contained in a DFF file loaded by [engineLoadDFF](/docs/engineLoadDFF.md "wikilink").

To replace weapon models you must use their object IDs, not weapon IDs. There is a weapon model list available at [weapons](/docs/weapons.md "wikilink").

Syntax
------

``` lua
bool engineReplaceModel ( dff theModel, int modelID [, bool alphaTransparency = false ] )
```

### Required Arguments

-   **theModel:** The model to replace the given model ID with
-   **modelID:** The model it to replace the model of

### Optional Arguments

-   **alphaTransparency:** Set to true to enable texture transparency within the model

### Returns

Returns *true* if the model was successfully replaced, *false* if it failed for some reason, ie. the DFF or the model ID is not valid.

Example
-------

**Example 1:**

<section name="Client" class="client" show="true">
Client-Side example for replacing vehicle model and texture with custom ones.

``` lua
function ReplaceVehicle ( )
outputChatBox ( "> replacing the euros vehicle" )

txd = engineLoadTXD ( "data/euros.txd" )
engineImportTXD ( txd, 587 )
dff = engineLoadDFF ( "data/euros.dff" )
engineReplaceModel ( dff, 587 )
end

addEvent ( "replaceVeh", true )
addEventHandler ( "replaceVeh", root, ReplaceVehicle )
```

</section>
<section name="Server" class="server" show="true">
Server-side example function for triggering the replace.

``` lua
function ReplaceCommand ( )
triggerClientEvent( "replaceVeh", root, replaceVeh )
end
addCommandHandler( "replace", ReplaceCommand )
```

</section>
**Example 2:**

<section name="Client" class="client" show="true">
Client-Side example for replacing object collision, texture and model with custom ones.

``` lua
function ReplaceObject ( )

col = engineLoadCOL( "MyModel.col" )
txd = engineLoadTXD( "MyModel.txd" )
dff = engineLoadDFF( "MyModel.dff", 0 )

engineReplaceCOL( col, 1234 )
engineImportTXD( txd, 1234 )
engineReplaceModel( dff, 1234 )-- replace the model at least

end

addEvent ( "replaceObj", true )
addEventHandler ( "replaceObj", root, ReplaceObject )
```

</section>
<section name="Server" class="server" show="true">
Server-side example function for triggering the replace.

``` lua
function ReplaceCommand ( )
triggerClientEvent( "replaceObj", root, replaceObj )
end
addCommandHandler( "replace", ReplaceCommand )
```

</section>
See Also
--------
