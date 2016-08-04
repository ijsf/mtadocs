This is an iteration function to traverse each single codepoint of a UTF-8 string.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence

### Optional Arguments

-   **charpos:** An integer representing the beginning position (offset will be added/subtracted).
-   **offset:** An integer representing the offset to charpos.

### Returns

Returns the *integer* position in bytes and the *integer* codepoint at this position, *nil* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example shows how to traverse a UTF-8 string the proper way without running into problems as in byte strings.

``` lua
for position, codepoint in utf8.next, "utf8-string" do
    print( "Codepoint @ ".. position .." = ".. codepoint )
end

for position, codepoint in utf8.next, "Как" do
    print( "Codepoint @ ".. position .." = ".. codepoint )
end
```

Output:

    // 1st iteration
    Codepoint @ 1 = 117
    Codepoint @ 2 = 116
    Codepoint @ 3 = 102
    Codepoint @ 4 = 56
    Codepoint @ 5 = 45
    Codepoint @ 6 = 115
    Codepoint @ 7 = 116
    Codepoint @ 8 = 114
    Codepoint @ 9 = 105
    Codepoint @ 10 = 110
    Codepoint @ 11 = 103

    // 2nd iteration
    Codepoint @ 1 = 1050
    Codepoint @ 3 = 1072
    Codepoint @ 5 = 1082

</section>
See Also
--------
