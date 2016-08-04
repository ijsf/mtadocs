This function is used to set the progress of a progressbar as a percentage.

Syntax
------

``` lua
bool guiProgressBarSetProgress ( progressBar theProgressbar, float progress )
```

### Required Arguments

-   **theProgressbar**: The progressbar you want to change the progress of
-   **progress**: a float ranging from 0 - 100

### Returns

Returns true if the progress was set, false otherwise.

Example
-------

This example sets the progress of a bar called “somebar” created with [guiCreateProgressBar](/guiCreateProgressBar.md "wikilink"), and outputs it to the chatbox.

``` lua
-- If the progressbar exsist then
if ( somebar ) then
    -- set the progress
        guiProgressBarSetProgress(somebar, 80)
        -- get the progress
    progress = guiProgressBarGetProgress(somebar)
    -- output to the chatbox
    outputChatBox ( "Current progress:" .. progress .. "%" )
else --if the progressbar was not found
       outputChatBox ("progressbar not found!")
       -- output a message
end
```

See Also
--------
