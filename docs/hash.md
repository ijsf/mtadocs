Syntax
------

``` lua
string hash ( string algorithm, string dataToHash )
```

### Required Arguments

-   **algorithm**: A string which must be one of these: “md5”, “sha1”, “sha224”, “sha256”, “sha384”, “sha512”
-   **dataToHash**: A string of the data to hash.

### Returns

Returns the hash of the data, false if an invalid argument was used.

Example
-------

``` lua
local myString = "myDatatoHash"
print(hash("md5", myString)) -- This will hash myString with the md5 Algorithm (it's equal to md5()) -> output: 0EF1E2203BD78182911B77EB6B9CC3DE

-- A another Example
local myNewString = "myNewDatatoHash"
print(hash("sha512", myNewString)) -- This will hash myNewString with the sha512 Algorithm -> output: 64A5678DC83EDCD8991E8CF0D69764663C0F933870BB89465F77B6C23D2A2B2400305A36D77404EE647D0D7B9D56CF7937B235BBD3885D08DCC62C81FB6D8429
```

See Also
--------

[ru:hash](/docs/ru-hash.md "wikilink")
