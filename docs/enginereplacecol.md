This function replaces the collision file of the given model id to the collision file passed. Use [engineLoadCOL](/docs/engineloadcol.md "wikilink") to load the collision file first.

**Note:** Collision libraries (.col files containing multiple collision models) are not supported. See [COL](/docs/col.md "wikilink") for details. Object models are supported only (no vehicles or players).

Syntax
------

``` lua
bool engineReplaceCOL ( col theCol, int modelID )
```

### Required Arguments

-   **theCol:** The collision file to replace with
-   **modelID:** The model ID whose collision file you want to replace

### Returns

Returns *true* if the collision was successfully replaced, *false* or *nil* if the collision could not be replaced for a reason.

Example
-------

<section name="Client" class="client" show="true">
Client-Side example for replacing object collision with custom one.

``` lua
function ReplaceCollision ( )
outputChatBox ( "> Replacing Collision Data." )
col = engineLoadCOL( "myColFile.col" )
engineReplaceCOL( col, 3356 )
end

addEvent ( "collisionReplace", true )
addEventHandler ( "collisionReplace", root, ReplaceCollision )
```

</section>
<section name="Server" class="server" show="true">
Server-side example function for triggering the replace.

``` lua
function ReplaceCols ( )
triggerClientEvent ( "collisionReplace", root, collisionReplace )
end
addCommandHandler("replacecol", ReplaceCols)
```

</section>
See Also
--------
