Calculates the MD5 hash of the specified string and returns its hexadecimal representation.

Note: returns an uppercase string, so make sure you string.upper() anything else you are checking against that has been MD5'd elsewhere.

Syntax
------

``` lua
string md5 ( string str )
```

### Required Arguments

-   **str:** the string to hash.

### Returns

Returns the MD5 hash of the input string if successful, *false* otherwise.

Example
-------

``` lua
function md5it (player,command, theString) -- open function
  if theString then -- check if the string is exist
    md5string = md5(theString) -- get the md5 string
    outputChatBox(theString.. " -> " .. md5string , player, 255, 0, 0, false) -- output it
  end
end
addCommandHandler ("md5it", md5it) -- create command
```

See Also
--------
