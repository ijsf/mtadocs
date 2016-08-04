This function is used to set the horizontal scroll position from a grid list

Syntax
------

``` lua
bool guiGridListSetHorizontalScrollPosition ( element guiGridlist, float fPosition )
```

### Required Arguments

-   **guiGridlist**: The grid list you want to set the horizontal scroll position from
-   **fPosition**: A float representing the horizontal scroll position (0-100)

### Returns

Returns *true* if the horizontal scroll position was set, or *false* otherwise.

Example
-------

This example sets the position of the horizontal scroll and outputs it to the chatbox.

``` lua
local gridList = guiCreateGridList(0.80, 0.10, 0.15, 0.60, true) -- Create the grid list
local column = guiGridListAddColumn(gridList, "New column", 1) -- Create a new column in the grid list
 
if gridList then -- if the grid list exist then
    guiGridListSetHorizontalScrollPosition (gridList,50) -- in the middle
    local postion = guiGridListGetHorizontalScrollPosition(gridList) -- get the horizontal scroll position
    outputChatBox ( "Current position of the horizontal scroll:" ..tostring(position).. "%" ) -- output to the chatbox
else 
    outputChatBox ("Grid list not found!") -- if the grid list was not found
end
```

Requirements
------------

See Also
--------
