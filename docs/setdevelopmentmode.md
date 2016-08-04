This function is used to set the development mode of the client. Setting development mode allows access to special commands which can assist with script debugging.

Development mode commands:

-   **[showcol](/docs/client_commands#showcol.md "wikilink")**: Enables colshapes to be viewed as a wireframe object.
-   **[showsound](/docs/client_commands#showsound.md "wikilink")**: Enables world sound ids to be printed in the debug output window.

Syntax
------

``` lua
bool setDevelopmentMode ( bool enable, [ bool enableWeb = false ] )
```

### Required Arguments

-   '''enable ''': A boolean to indicate whether development mode is on (true) or off (false)

### Returns

Returns *true* if the mode was set correctly, *false* otherwise.

Requirements
------------

Example
-------

**Example 1:** This example would set the development mode of the client. Use /showcol \[&lt;0-1&gt;\] and /showsound \[&lt;0-1&gt;\] later to enable/disable respective funtions.

``` lua
addCommandHandler( "devmode",
function ()
    setDevelopmentMode ( true )
end
)
```

See Also
--------
