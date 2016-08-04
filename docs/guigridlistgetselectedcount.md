This function returns the amount of options selected in the specified [grid list](/docs/Element/GUI/Gridlist.md "wikilink").

Syntax
------

``` lua
int guiGridListGetSelectedCount ( element gridList )
```

### Required Arguments

-   **gridList:** The [grid list](/docs/Element/GUI/Gridlist.md "wikilink") which amount of selected items you want to retrieve.

### Returns

Returns an [integer](/docs/int.md "wikilink") representing the amount of selected options if everything was successful or *false* if invalid arguments were passed.

Example
-------

This example creates a gridlist filled with players names then check who has the letter “a” in their name, after it selects everyone who has the letter “a” then it outputs the selected rows. TESTED!

``` lua
    gridlist = guiCreateGridList(100,100,200,100,false)
    guiGridListAddColumn(gridlist,"Players",0.50)
    for i,v in ipairs(getElementsByType("player"))do
        guiGridListSetItemText(gridlist,guiGridListAddRow(gridlist),1,getPlayerName(v),false,false)
    end
    for b=0, guiGridListGetRowCount(gridlist)do
        if(string.find(guiGridListGetItemText(gridlist,b,1),"a",1,true))then
            guiGridListSetSelectedItem(gridlist,b,1)
        end
    end
    outputChatBox("The number of Players with 'a' in their name: "..guiGridListGetSelectedCount(gridlist)..".")
```

See Also
--------
