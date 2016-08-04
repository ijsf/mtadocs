Inserts a substring into input string. If insert-position is given, the substring will be inserted before the character at this index, otherwise the substring will concatenate to input. The insert position may be negative.

Syntax
------

``` lua
, string substring )
```

### Required Arguments

-   **input:** A string character sequence
-   **substring:** A string character sequence which should be inserted

### Optional Arguments

-   **insert\_pos:** An integer representing the position, where the substring will be inserted at.

### Returns

Returns a *string* with the inserted substring value.

Example
-------

<section name="Server" class="server" show="true">
This example shows a command handler for '/insert \[something\]', which will concatenate the '\[something\]' after the 'hello ' string in 2 ways.

``` lua
addCommandHandler("insert", 
    function (player, command, word)
        if word then
            local output = utf8.insert( "hello ", word )
            outputChatBox( output, player )
            
            local output = utf8.insert( "hello ", utf8.len( "hello " ) + 1, word )
            outputChatBox( output, player )
        end
    end
)
```

</section>
See Also
--------
