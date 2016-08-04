This function loads a RenderWare Texture Dictionary (TXD) file into GTA. The texture dictionary can then be used to provide textures.

This is a client side function. Be sure to transfer your TXD file by including it in the meta file.

Syntax
------

``` lua
txd engineLoadTXD ( string txd_file / string raw_data [, bool filteringEnabled = true ] )
```

[thumb|Difference between texture filtering modes (left = filtering disabled, right = filtering enabled).|284x230px](/docs/Image:Filtering.jpg.md "wikilink")

### Required Arguments

-   **txd\_file / raw\_data:** The [filepath](/docs/filepath.md "wikilink") to the TXD file you want to load or whole data buffer of the TXD file.

### Optional Arguments

-   **filteringEnabled:** Whether to enable texture filtering.

### Returns

Returns a [TXD](/docs/TXD.md "wikilink") if the file was loaded, *false* otherwise.

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

**Example 2:** This example loads a combination of custom COL, TXD and DFF files to replace an in-game model of a set of floors.

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
