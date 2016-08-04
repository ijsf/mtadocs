Extract substrings by matching patterns in the input string. This function can be used to extract specific information from a string.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence
-   **pattern:** A string match [pattern](http://lua-users.org/wiki/PatternsTutorial)

### Optional Arguments

-   **index:** An integer representing the beginning position for the pattern matching

### Returns

Returns a sequence of *string* matches from the **input** string, *nil* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example shows how to extract values from an input string by using a pattern to match the value parts.

``` lua
local input = "Level: 5, Rank: General, 128.42 points"
local level, rank, points = utf8.match( input, "Level: (%d+), Rank: (.-), (%d+.?%d*) points" )
level, points = tonumber( level ), tonumber( points )

print( level, rank, points ) -- 5, General, 128.42
```

</section>
See Also
--------
