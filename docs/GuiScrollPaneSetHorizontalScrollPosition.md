This function is used to set the position of a horizontal scroll pane as a percentage.

Syntax
------

``` lua
bool guiScrollPaneSetHorizontalScrollPosition ( element horizontalScrollPane, float position )
```

### Required Arguments

-   **horizontalScrollPane**: The scroll pane you want to change the position of
-   **position**: a float ranging from 0 - 100

### Returns

Returns **true** if the position was set, **false** otherwise.

Example
-------

This example sets the position of a scroll pane called “myScrollPane” created with [guiCreateScrollPane](/guiCreateScrollPane.md "wikilink"), and outputs it to the chatbox.

``` lua
if ( myScrollPane ) then -- if the scroll pane exist then
    -- set the position
        guiScrollPaneSetHorizontalScrollPosition( myScrollPane, 100 ) -- right end
        -- get the position
    local position = guiScrollPaneGetHorizontalScrollPosition( myScrollPane )
    -- output to the chatbox
    outputChatBox ( "Current position of scroll pane:" .. tostring(position) .. "%" )
else -- if the scroll pane was not found
       outputChatBox ("scroll pane not found!")
end
```

See Also
--------
