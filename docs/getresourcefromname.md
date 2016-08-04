This function is used to retrieve a resource from its name. A resource's name is the same as its folder or file archive name on the server (without the extension).

Syntax
------

``` lua
resource getResourceFromName ( string resourceName )
```

### Required Arguments

-   **resourceName:** the name of the resource you wish to get.

### Returns

Returns the *resource* with the specified name, or *false* if no resource of that name exists.

Example
-------

<section name="Server" class="server" show="true">
This example prints out a message to the chatbox when a resource named *playerblips* is started.

``` lua
function onStart( theResource )
     local blipsResource = getResourceFromName ( "playerblips" ) -- get the resource of name "playerblips"
     if ( blipsResource and theResource == blipsResource ) then -- check if the resource started was it
          outputChatBox ( "Blips resource started!" )
     end
end
addEventHandler ( "onResourceStart", getRootElement(), onStart )
```

</section>
See Also
--------
