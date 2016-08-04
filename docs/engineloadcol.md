This function loads a RenderWare Collision (COL 1/2/3) file into GTA. The collisions can then be used to provide collisions for in-game objects.

For vehicles, please omit this function by embedding your [COL](/docs/col.md "wikilink") file into your [DFF](/DFF.md "wikilink") file. This way, you can be sure that the COL file is correctly (and automatically) loaded when calling [engineLoadDFF](/engineLoadDFF.md "wikilink").

This is a client side function. Be sure to transfer your COL file by including it in the meta file.

**Note:** collision libraries (.col files containing multiple collision models) are not supported. See [COL](/docs/col.md "wikilink") for details.

Syntax
------

``` lua
col engineLoadCOL ( string col_file / string raw_data ) 
```

### Required Arguments

-   **col\_file / raw\_data:** The [filepath](/docs/filepath.md "wikilink") to the [COL](/COL.md "wikilink") file you want to load or whole data buffer of the COL file.

### Returns

Returns a [COL](/docs/col.md "wikilink") if the file was loaded, *false* otherwise.

Example
-------

**Example 1:** This example loads a combination of a custom DFF and TXD file to replace the Euros vehicle in-game. The collisions are embedded inside the DFF file.

``` lua
outputChatBox ( "> replacing the euros vehicle" )

txd = engineLoadTXD ( "data/euros.txd" )
engineImportTXD ( txd, 587 )
dff = engineLoadDFF ( "data/euros.dff" )
engineReplaceModel ( dff, 587 )
```

**Example 2:** This example loads a combination of custom COL, TXD and DFFfiles to replace an in-game model of a set of floors.

``` lua
outputChatBox ( "> loading floor objects" )
col_floors = engineLoadCOL ( "models/office_floors.col" )
engineReplaceCOL ( col_floors, 3781 )
txd_floors = engineLoadTXD ( "models/office_floors.txd" )
engineImportTXD ( txd_floors, 3781 )
dff_floors = engineLoadDFF ( "models/office_floors.dff" )
engineReplaceModel ( dff_floors, 3781 )
```

Changelog
---------

See Also
--------
