Checks whether a ped has a certain control pressed.

Syntax
------

``` lua
bool getPedControlState ( ped thePed, string control )
```

### Required Arguments

-   **thePed:** the ped you want to check.
-   **control:** the control to get the status of. See [control names](/control_names.md "wikilink") for a list of valid names.

### Returns

Returns *true* if the ped is pressing the specified control, *false* if not or an invalid argument was passed.

See Also
--------
