This function removes a substring in a UTF-8 string by using a position range.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence
-   **start:** An integer representing the beginning position.

### Optional Arguments

-   **stop:** An integer representing the ending position.

### Returns

Returns the *string* with the removed substring from the range.

Example
-------

<section name="Server" class="server" show="true">
This example shows how to remove substrings from strings.

``` lua
-- Keep the first and last character
local input = "яблоко"
local output = utf8.remove( input, 2, -2 ) 
print( output ) -- яо

-- Remove the last character
local input = "Банан"
local output = utf8.remove( input, -1, -1 )
print( output ) -- Бана
```

</section>
See Also
--------
