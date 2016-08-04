This function returns the current input mode as set by [guiSetInputMode](/guiSetInputMode.md "wikilink"). Default mode is *“allow\_binds”*.

Syntax
------

``` lua
string guiGetInputMode ( )
```

### Returns

Returns a string defining the current input mode, potential values are:

-   **“allow\_binds”:** binds are enabled, hence using a key such as t in an editbox will still activate the chatbox
-   **“no\_binds”:** binds are disabled, hence using a key such as t in an editbox will not activate the chatbox
-   **“no\_binds\_when\_editing”:** binds are always enabled except when an editable editbox or memo has input focus

Example
-------

<section name="Client" class="client" show="true">
``` lua
addCommandHandler( "checkmode", 
function ()
    outputChatBox( string.format( "The current input mode is: '%s'", guiGetInputMode () ) )
end )
```

</section>
Note
----

This function, introduced in 1.1, is **not** a replacement of [guiGetInputEnabled](/guiGetInputEnabled.md "wikilink"), indeed for the mode *“no\_binds\_when\_editing”* the actual state of binds depends on the currently focused GUI widget. However:

-   when *guiGetInputMode ( )* returns *“allow\_binds”* you can be sure that *guiGetInputEnabled ()* will return *false*
-   when *guiGetInputMode ( )* returns *“no\_binds”* you can be sure that *guiGetInputEnabled ()* will return *true*

See Also
--------
