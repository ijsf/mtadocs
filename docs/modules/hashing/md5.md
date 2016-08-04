Calculate the **MD5** hash of a string

Syntax
------

``` lua
string md5( string str )
```

### Required arguments

-   **str:** string of which you want to calculate the hash

### Returns

String containing calculated MD5 hash of **str** or nil if **str** wasn't string

Example
-------

**Example:** This calculates the hash of **“hello world”** and prints it in debug window

``` lua
hash = md5( "hello world" ) -- calculate MD5 hash of "hello world"
outputDebugString( hash )
```

See also
--------
