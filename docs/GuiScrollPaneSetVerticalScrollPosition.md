This function is used to set the position of a vertical scroll pane as a percentage.

Syntax
------

``` lua
bool guiScrollPaneSetVerticalScrollPosition ( element verticalScrollPane, float position )
```

### Required Arguments

-   **verticalScrollPane**: The scroll pane you want to change the position of
-   **position**: a float ranging from 0 - 100

### Returns

Returns **true** if the position was set, **false** otherwise.

Example
-------

This example sets the position of a scroll pane called “myScrollPane” created with [guiCreateScrollPane](/guiCreateScrollPane.md "wikilink"), and outputs it to the chatbox.

``` lua
if ( myScrollPane ) then -- if the scroll pane exist then
    -- set the position
        guiScrollPaneSetVerticalScrollPosition( myScrollPane, 33.3 ) -- 1/3 from the upside
        -- get the position
    local position = guiScrollPaneGetVerticalScrollPosition( myScrollPane )
    -- output to the chatbox
    outputChatBox ( "Current position of scroll pane:" .. tostring(position) .. "%" )
else -- if the scroll pane was not found
       outputChatBox ("scroll pane not found!")
end
```

See Also
--------
