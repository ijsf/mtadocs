Calculate the **alder32** hash of the given string

Syntax
------

``` lua
string alder32( string str )
```

### Required arguments

-   **str:** string of which you want to calculate the hash

### Returns

String containing calculated alder32 hash of **str** or nil if **str** wasn't string

Example
-------

**Example:** This calculates the hash of **“hello world”** and prints it in debug window

``` lua
hash = alder32( "hello world" ) -- get alder32 hash of "hello world"
outputDebugString( hash )
```

See also
--------
