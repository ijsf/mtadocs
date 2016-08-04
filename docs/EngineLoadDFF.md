This function loads a RenderWare Model (DFF) file into GTA.

To successfully load your model with textures, be sure to use [engineLoadTXD](/engineLoadTXD.md "wikilink") and [engineImportTXD](/engineImportTXD.md "wikilink") before calling this function. If some error occurs while loading the DFF, MTA will output a message - check out [DFF error messages](/DFF_error_messages.md "wikilink") to know what they mean.

This is a client side function. Be sure to transfer your DFF file by including it in the meta file.

The returned [DFF](/DFF.md "wikilink") element is an element in the element tree, just like vehicles and objects. When the dff is destroyed, ie on resource unload or using [destroyElement](/destroyElement.md "wikilink"), any elements that use the DFF, such as vehicles or objects will be reset.

Syntax
------

``` lua
dff engineLoadDFF ( string dff_file / string raw_data ) 
```

### Required Arguments

-   **dff\_file / raw\_data:** The [filepath](/filepath.md "wikilink") to the DFF file you want to load or whole data buffer of the DFF file.

### Returns

Returns a [DFF](/DFF.md "wikilink") element if the dff file loaded, *false* otherwise.

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

**Example 2:** This example loads a combination of custom TXD, COL and DFF files to replace an in-game model of a set of floors.

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
