The function gets the real length of a string, in characters.

Syntax
------

``` lua
int utfLen ( string theString )
```

### Required Arguments

-   **theString:** The [string](/docs/string.md "wikilink") to get the length of.

### Returns

Returns an *[int](/docs/int.md "wikilink")* if the function was successful, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example adds a command *russian\_text\_length* which prints out a length russian text.

``` lua
addCommandHandler( 'russian_text_length',
    function( )
        outputChatBox( string.format( 'Russian text length is: %d', utfLen( 'Текст' ) ) )
    end
)
```

</section>
See Also
--------
