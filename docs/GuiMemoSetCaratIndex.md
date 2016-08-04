This function sets the current position of the caret (the text cursor) within the memo.

Syntax
------

``` lua
bool guiMemoSetCaratIndex ( gui-memo theMemo, int index )
```

### Required Arguments

-   **theMemo:** The memo edit box where the caret position is to be changed.
-   **index:** An integer referring to the desired position within the box.

### Returns

Returns *true* if the caret was successfully moved, *false* otherwise.

See Also
--------
