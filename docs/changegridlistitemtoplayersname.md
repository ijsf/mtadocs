<pageclass class="#228B22" subcaption="Useful Function"></pageclass> <lowercasetitle/>

This function will change gridlist items and values to players name.

Syntax
------

``` lua
bool changeGridListItemToPlayersName ( element GridList, element Column )
```

### Required Arguments

-   **GridList**: GridList you want to edit it.
-   **Column**: Column you want to change the items.

Code
----

<section name="Function source" class="client" show="true">
``` lua
changeGridListItemToPlayersName = function ( GridList, Column )
    if GridList and Column then -- Check Parematers
        if getElementType ( GridList ) == "gui-gridlist" then -- Check The Type of ' GridList '
            if guiGridListClear ( GridList ) then
                for i, v in next, getElementsByType ( "player" ) do -- Get Everything by Type ' player ' 
                    guiGridListSetItemText ( GridList, guiGridListAddRow ( GridList ), Column, getPlayerName ( v ), false, false );
                end;
            end;
        end;
    end;
end;
```

</section>
Example
-------

<section name="Client-side example" class="client" show="true">
This Example will add players name to the gridlist.

``` lua
wnd = guiCreateWindow ( 100, 100, 400, 400, "Test", false ); -- Create Window
grid = guiCreateGridList ( 25, 30, 350, 350, false, wnd ); -- Create Gridlist
col = guiGridListAddColumn ( grid, "Players", 0.9 ); -- Create Column
changeGridListItemToPlayersName ( grid, col ); -- Set Gridlist Values
```

</section>
-   This Function Has Created By **3NAD**.

See Also
--------

[Category:Useful Functions](/docs/Category:Useful_Functions.md "wikilink")
