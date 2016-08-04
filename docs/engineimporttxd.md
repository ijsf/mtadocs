This function imports (adds) a loaded RenderWare Texture Dictionary into a specific model. This is necessary in order for the DFF loader to find any new textures. Please **call this function before loading the DFF model file**, in order to allow the DFF loading process to find the new textures. This function can also replace default GTA textures, so that it becomes possible to e.g. put custom images on existing billboards. Ped and weapon textures are also supported.

See here for [tips on reducing the size of TXD files](/docs/optimize_custom_txd.md "wikilink").

Syntax
------

``` lua
bool engineImportTXD ( txd texture, int model_id ) 
```

### Required Arguments

-   **texture:** The [TXD](/docs/txd.md "wikilink") that was loaded with [engineLoadTXD](/engineLoadTXD.md "wikilink")
-   **model\_id:** The model id to import the TXD into

### Returns

Returns *true* if the function executed succesfully, *false* otherwise.

Example
-------

**Example 1:** This example loads a combination of a custom TXD and DFF file to replace the Euros vehicle in-game. The collisions are embedded inside the DFF file.

``` lua
outputChatBox ( "> replacing the euros vehicle" )

txd = engineLoadTXD ( "data/euros.txd" )
engineImportTXD ( txd, 587 )
dff = engineLoadDFF ( "data/euros.dff" )
engineReplaceModel ( dff, 587 )
```

**Example 2:** This example loads a combination of custom COL, TXD and DFF files to replace an in-game model of a set of floors.

``` lua
outputChatBox ( "> loading floor objects" )
col_floors = engineLoadCOL ( "models/office_floors.col" )
engineReplaceCOL ( col_floors, 3781 )
txd_floors = engineLoadTXD ( "models/office_floors.txd" )
engineImportTXD ( txd_floors, 3781 )
dff_floors = engineLoadDFF ( "models/office_floors.dff")
engineReplaceModel ( dff_floors, 3781 )
```

**Example 3:** This example replaces the victim billboards in last venturas (when replacing default models you do not need to replace a COL or DFF)

``` lua
outputChatBox ( "> replacing billboards" )
txd_billboards = engineLoadTXD ( "models/vgsn_billboard.txd" )
engineImportTXD ( txd_billboards, 7300 )
```

**Example 4:** This example shows that you only need to load a TXD once, even if you want to replace several different textures

``` lua
outputChatBox ( "> replacing billboards" )
txd_billboards = engineLoadTXD ( "models/vgsn_billboard.txd" )
engineImportTXD ( txd_billboards, 7300 )
engineImportTXD ( txd_billboards, 7301 )
engineImportTXD ( txd_billboards, 7302 )
engineImportTXD ( txd_billboards, 7303 )
```

See Also
--------
