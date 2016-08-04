This function destroys a [textitem](/textitem.md "wikilink") object.

Syntax
------

``` lua
void textDestroyTextItem ( textitem theTextitem )             
```

### Required Arguments

-   **theTextitem:** The text item you wish to destroy.

Example
-------

This example creates then destroys a [textitem](/textitem.md "wikilink").

``` lua
-- Create a new text item
text = textCreateTextItem ( "Hello, world!" )
-- Destroy it
textDestroyTextItem ( text )
```

See Also
--------
