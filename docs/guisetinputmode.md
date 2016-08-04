This function controls the input mode to define whether or not (and when) keybinds or MTA binds are overridden (disabled) so that text can be input into an editbox, for example. The binds can be either:

-   never disabled (hence using a key such as t in an editbox will still activate the chatbox)
-   always disabled (hence using a key such as t in an editbox will not activate the chatbox)
-   only disabled when actually editing an editbox or a memo (binds are always enabled except when an editbox or memo has input focus)

Syntax
------

``` lua
bool guiSetInputMode ( string mode )
```

### Required Arguments

-   **mode:** a string representing the desired input mode. Accepted values are:
    -   **“allow\_binds”:** binds are enabled, hence using a key such as t in an editbox will still activate the chatbox (default)
    -   **“no\_binds”:** binds are disabled, hence using a key such as t in an editbox will not activate the chatbox
    -   **“no\_binds\_when\_editing”:** binds are always enabled except when an editable editbox or memo has input focus

### Returns

Returns *true* if input mode could be changed, *false* if invalid parameters are passed.

Example
-------

``` lua
addEventHandler("onClientResourceStart", getResourceRootElement(),
function()
    guiSetInputMode("no_binds_when_editing") --Calls guiSetInputMode once and for all to not have to handle binds state dynamically
end)
```

Note
----

This function, introduced in 1.1, can be used as a replacement of [guiSetInputEnabled](/docs/guisetinputenabled.md "wikilink") since it provides the same functionality with one added feature.

-   *guiSetInputEnabled ( false )* is the same as *guiSetInputMode ( “allow\_binds” )*
-   *guiSetInputEnabled ( true )* is the same as *guiSetInputMode ( “no\_binds” )*

See Also
--------
