This function can be used to retrieve all the [players](/docs/player.md "wikilink") currently observing a specified [textdisplay](/docs/textdisplay.md "wikilink").

Syntax
------

``` lua
table textDisplayGetObservers ( textdisplay theDisplay )
```

### Required Arguments

-   **theDisplay**: The [textdisplay](/docs/textdisplay.md "wikilink") of which observers you want to get.

### Returns

Returns a [table](/docs/table.md "wikilink") of players that are observers of the display or *false* if invalid textdisplay is passed.

Example
-------

``` lua

function removeAllObservers ( player , command )
    local tObservers = textDisplayGetObservers ( serverDisplay ) -- get a table of all observers in 'serverDisplay' text display
    if tObservers then -- if got the table
        for index,player in ipairs ( tObservers ) do -- loop the table
            textDisplayRemoveObserver ( serverDisplay , player ) -- remove the player from the text display
        end
    end
end
addCommandHandler("removeAllObservers",removeAllObservers)
```

See Also
--------
