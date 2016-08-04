Reverses the input string.

Syntax
------

``` lua
string utf8.reverse ( string input )
```

### Required Arguments

-   **input:** A string character sequence

### Returns

Returns a *string* containing the reversed original UTF-8 string.

Example
-------

<section name="Client" class="client" show="true">
This example shows how to reverse a UTF-8 string.

``` lua
local input = "今日は素晴らしい日です"
local output = utf8.reverse( input )
outputConsole( output ) -- すで日いしら晴素は日今
```

</section>
See Also
--------
