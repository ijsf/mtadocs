This function gets the ID of an element. This is the “id” attribute of the element and is a string, NOT a number like a model ID, weapons ID or similar.

Syntax
------

``` lua
string getElementID ( element theElement ) 
```

### Required Arguments

-   **theElement:** the element from which to retrieve the ID.

### Returns

This returns a *string* containing the element ID. It will return an empty *string* if it has no ID. It will return *false* if the element is invalid.

Example
-------

To get the ID of the following element:

``` xml
<flag id="northflag" posX="2365" posY="215" posZ="32" />
```

You could use the following code:

``` lua
-- assume flag refers to the flag element in the above XML code
idstring = getElementID ( flag )                   -- get the id of the flag element
outputChatBox ( "The flag's ID is: " .. idstring ) -- output: The flag's ID is: northflag
```

See Also
--------

[de:GetElementID](/docs/de:getelementid.md "wikilink")
