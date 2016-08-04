This function gets the progress of a progress bar as a percentage

Syntax
------

``` lua
float guiProgressBarGetProgress ( progressBar theProgressbar )
```

### Required Arguments

-   **theProgressbar**: The progressbar you want to check.

### Returns

Returns a [float](/float.md "wikilink") ranging between 0 and 100.

Example
-------

This example gets the progress of a bar called “somebar” created with [guiCreateProgressBar](/guiCreateProgressBar.md "wikilink"), and outputs it to the chatbox.

``` lua
-- If the progressbar exsist then
if ( somebar ) then
    -- get the progress
    progress = guiProgressBarGetProgress(somebar)
    -- output to the chatbox
    outputChatBox ( "Current progress:" .. progress .. "%" )
end
```

See Also
--------
