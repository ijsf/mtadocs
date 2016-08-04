This function returns a pattern finding iterator for UTF-8 strings. The iterator will search through the string **input** looking for instances of the pattern you passed. For more information on iterators read the [ForTutorial](http://lua-users.org/wiki/ForTutorial) and [IteratorsTutorial](http://lua-users.org/wiki/IteratorsTutorial).

Syntax
------

``` lua
iterator utf8.gmatch ( string input, string pattern )
```

### Required Arguments

-   **input:** A string character sequence
-   **pattern:** A string match [pattern](http://lua-users.org/wiki/PatternsTutorial)

### Returns

Returns an *function* for iterations on the **input** string by using the passed **pattern** string.

Example
-------

<section name="Server" class="server" show="true">
This example prints every word in the UTF-8 string

``` lua
for word in utf8.gmatch( "Как вас зовут?", "%a+" ) do 
    print( word )
end
```

Output:

    Как
    вас
    зовут

</section>
See Also
--------
