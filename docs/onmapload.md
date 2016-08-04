This event is triggered when a map is loaded.

Syntax
------

``` lua
void onMapLoad ( string name )
```

Variables
---------

-   The source of this event refers to the loaded map.
-   **name**: A string representing the name of the map

Example
-------

This example displays a message in the textbox when you load a map containing this lua

``` lua
addEventHandler ( "onMapLoad", getRootElement(), "mapLoadChatBoxOutput" )
function mapLoadChatBoxOutput ( name )
    outputChatBox ( "Map "..name.." Loaded", root, 255, 255, 255 )
end
```

See Also
--------
