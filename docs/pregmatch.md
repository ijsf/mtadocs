Syntax
------

``` lua
table pregMatch ( string base, string pattern [, int/string flags = 0, int maxResults = 100000 ] )
```

### Required Arguments

-   **base:** The base [string](/docs/string.md "wikilink") for replace.
-   **pattern:** The pattern for match in base string.

### Optional Arguments

-   **flags:** Conjuncted value that contains flags ( 1 - ignorecase, 2 - multiline, 4 - dotall, 8 - extended ) or ( i - Ignore case, m - Multiline, d - Dotall, e - Extended )
-   **maxResults:** Maximum number of results to return

### Returns

Returns a *[table](/docs/table.md "wikilink")* if one or more match is found, *false* otherwise.

Example
-------

<section name="Shared ( client and server )" class="both" show="true">
Some examples:

``` lua
addCommandHandler( 'example',
    function( )
                --[[
                Will print:
                Match: 1, hello
                Match: 2, hello
                ]] 
                for i, v in ipairs( pregMatch( "hello hello", "(hello)"  ) ) do
                outputDebugString( "Match: " .. i .. ", " .. v );
                end
    end
);

addCommandHandler( 'example2',
    function( )
                --[[
                Will print:
                Match: 1, somebodyWWw
                Match: 2, 228
                ]] 
                for i, v in ipairs( pregMatch( "somebodyWWw\n228", "([a-z0-9]+)", "im" ) ) do
                outputDebugString( "Match: " .. i .. ", " .. v );
                end
    end
);
```

</section>
Requirements
------------

See Also
--------
