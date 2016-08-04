This function removes a set rule value that can be viewed by server browsers.

Syntax
------

``` lua
bool removeRuleValue ( string key )              
```

### Required Arguments

-   **key:** The name of the rule you wish to remove

### Returns

Returns *true* if the rule value was removed, *false* if it failed.

Example
-------

This example shows how you could set a rule that shows that your script is running on the server.

``` lua
removeRuleValue ( "myScriptRunning" )
```

See Also
--------
