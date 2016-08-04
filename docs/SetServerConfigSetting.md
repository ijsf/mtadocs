This function sets server settings which are stored in the [mtaserver.conf](/Server_mtaserver.conf.md "wikilink") file.

Note: This function is protected by default and must be explicitly allowed in the servers acl before it can be used.

Syntax
------

``` lua
bool setServerConfigSetting ( string name, string value, [ bool bSave = false ] )
```

### Required Arguments

-   **name :** The name of the setting. Only certain settings from [mtaserver.conf](/Server_mtaserver.conf.md "wikilink") can be changed with this function. These are:
    -   minclientversion
    -   recommendedclientversion
    -   password
    -   fpslimit - (0-100)
    -   networkencryption - 0 for off, 1 for on
    -   bandwidth\_reduction - “none”, “medium”, “maximum” Set to maximum for less bandwidth usage (medium is recommended for race servers)
    -   player\_sync\_interval - See [Sync\_interval\_settings](/Sync_interval_settings.md "wikilink") for all \*\_sync\_interval settings
    -   lightweight\_sync\_interval
    -   camera\_sync\_interval
    -   ped\_sync\_interval
    -   unoccupied\_vehicle\_sync\_interval
    -   keysync\_mouse\_sync\_interval
    -   keysync\_analog\_sync\_interval
    -   bullet\_sync
-   **value:** The value of the setting

### Optional Arguments

-   **bSave:** Set to *true* to make the setting permanent, or *false* for use only until the next server restart.

### Returns

Returns *true* if the setting was successfully set, or *false* otherwise.

Example
-------

This example enables network encryption

``` lua
setServerConfigSetting( "networkencryption", "1", true )
```

See Also
--------
