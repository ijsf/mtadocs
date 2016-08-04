This function retrieves the analog control state of a ped, as set by [setPedAnalogControlState](/setPedAnalogControlState.md "wikilink").

Syntax
------

``` lua
float getPedAnalogControlState ( ped thePed, string controlName )
```

### Required Arguments

-   **thePed:** The ped you wish to retrieve the control state of.
-   **controlName:** The control. See [control names](/control_names.md "wikilink") for a list of possible controls.

### Returns

Returns a float between 0 ( full release ) and 1 ( full push ) indicating the amount the control is pushed.

Example
-------

``` lua
-- todo
```

Requirements
------------

See Also
--------
