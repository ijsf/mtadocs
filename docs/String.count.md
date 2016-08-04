This function counts how many times a string is found from within another string.

Syntax
------

``` lua
int string.count(string text, string search)
```

### Required Arguments

-   **text:** A string to find the text from
-   **search:** A string defining what to find

Code
----

``` lua
function string.count (text, search)
    if ( not text or not search ) then return false end
    
    return select ( 2, text:gsub ( search, "" ) );
end
```

Created by Krischkros, Edited by nextz.

Example
-------

This example outputs the result of this function to the chat.

``` lua
outputChatBox( string.count( "Just a test string", "t" ) ) -- and the result is 4!
```

See also
--------
