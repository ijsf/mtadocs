This function retrieves server settings which are usually stored in the **mtaserver.conf** file.

Syntax
------

``` lua
string getServerConfigSetting ( string name )
```

### Required Arguments

-   **name :** The name of the setting

### Returns

Returns a string containing the current value for the named setting, or *false* if the setting does not exist.

Example
-------

This example prints the server minimum allowed client version to the chatbox

``` lua
outputChatBox( getServerConfigSetting ("minclientversion") )
```

See Also
--------
