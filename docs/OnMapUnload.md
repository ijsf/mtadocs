This event is triggered when the map is changed or unloaded.

Example
-------

This example displays a message in the textbox when the map is changed / unloaded

``` lua

addEventHandler ( "onMapUnload", root, "onMapUnload" )
function onMapUnload ( )
  outputChatBox ( "Script Unloaded!", root, 255, 255, 255 )
end
```

See also
--------
