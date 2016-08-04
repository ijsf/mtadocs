This function is used to set the vertical scroll position from a grid list

Syntax
------

``` lua
bool guiGridListSetVerticalScrollPosition( element guiGridlist, float fPosition )
```

### Required Arguments

-   **guiGridlist**: The grid list you want to set the vertical scroll position from
-   **fPosition**: A float representing the vertical scroll position (0-100)

### Returns

Returns *true* if the vertical scroll position was set, or *false* otherwise.

Requirements
------------

Example
-------

This example sets the position of the vertical scroll and outputs it to the chatbox.

``` lua
local gridList = guiCreateGridList(0.80, 0.10, 0.15, 0.60, true) -- Create the grid list
local column = guiGridListAddColumn(gridList, "New column", 1) -- Create a new column in the grid list
 
if gridList then -- if the grid list exist then
    guiGridListSetVerticalScrollPosition (gridList,50) -- in the middle
    local postion = guiGridListGetVerticalScrollPosition(gridList) -- get the vertical scroll position
    outputChatBox ( "Current position of the vertical scroll:" ..tostring(position).. "%" ) -- output to the chatbox
else 
    outputChatBox ("Grid list not found!") -- if the grid list was not found
end
```

See Also
--------
