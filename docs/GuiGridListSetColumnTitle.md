This function is used to change the column title of a gridlist column.

Syntax
------

``` lua
bool guiGridListSetColumnTitle( element guiGridlist, int columnIndex, string title )
```

### Required Arguments

-   **guiGridlist**: The grid list you want to change the column title from
-   **columnIndex**: Column ID
-   **title**: The title of the column

### Returns

Returns *true* if the new title was set, or *false* otherwise.

Requirements
------------

Example
-------

``` lua
local gridlist = guiCreateGridList ( 332, 195, 286, 249, false ) 
local column = guiGridListAddColumn(gridlist, "title", 0.5)

addCommandHandler("setTitle",
   function(cmd, title)
     if title then 
       if column then 
          guiGridListSetColumnTitle(gridlist ,column, title)    
      outputChatBox("Column name has been successfully changed to : "..title,0,255,0)
       end 
     else
       outputChatBox("[Usage] /setTitle [title]",255,0,0)
     end
  end
)
```

See Also
--------
