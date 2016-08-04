This function gets a setting's value, or a group of settings' values, from the [settings registry](/docs/settings_system.md "wikilink").

*Note: Your settings cannot have a period (.) in them. This character is reserved. Read below for more details.*

Syntax
------

``` lua
var get ( string settingName )
```

Optional Arguments
------------------

**settingName:** The name of the setting you want to set. See [setting names](/docs/settings_system#setting_names.md "wikilink") for information on settings names.

### Returns

Returns the value of the setting if a single setting was specified and found, or a *table* (in associative-array form) containing:

-   the list of global setting name/value pairs if "." is passed as a setting name,
-   the list of resource settings if a resource name followed by a "." is passed,
-   the list of the script's resource settings if an empty string is passed.

It returns *false* if the specified setting or settings group doesn't exist, or if the settings group you are trying to retrieve doesn't have any public or protected settings.

Example
-------

Example returns a value from the settings registry with the name “respawnTime”.

``` lua
function getMySetting()
    if get ( "respawnTime" ) then
        return get ( "respawnTime" )
    end
    return false
end
```

See Also
--------

[ru:get](/docs/ru-get.md "wikilink")
