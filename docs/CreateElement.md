This function is used to create a new dummy element in the [element tree](/element_tree.md "wikilink") which do not necessarily represent an entity within the San Andreas world. A common use for this function is for creating custom elements, such as a Flag or a Base.

Elements created using this function are placed in the element tree with their parent as the 'dynamic' map element.

Syntax
------

``` lua
element createElement ( string elementType, [ string elementID = nil ] )
```

### Required Arguments

-   **elementType:** The type of element being created.

### Optional Arguments

-   **elementID:** The ID of the element being created.

### Returns

Returns the element if it was successfully created. Returns *false* if the arguments are wrong.

Example
-------

This example creates a “flag” element, named “blue”, which will be at the resource's dynamic map.

``` lua
blueTeamFlag = createElement( "flag", "blue" )
```

Except for it being placed in a different map root, that line will have the same effect as having this in a .map file:

``` xml
<flag id="blue" />
```

See Also
--------
