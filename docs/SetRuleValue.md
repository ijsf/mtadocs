This function sets a rule value that can be viewed by server browsers.

Syntax
------

``` lua
bool setRuleValue ( string key, string value )              
```

### Required Arguments

-   **key:** The name of the rule
-   **value:** The value you wish to set for the rule

### Returns

Returns *true* if the rule value was set, *false* if invalid arguments were specified.

Example
-------

This example shows how you could set a rule that shows that your script is running on the server.

``` lua
setRuleValue ( "myScriptRunning", "yes" )
```

See Also
--------
