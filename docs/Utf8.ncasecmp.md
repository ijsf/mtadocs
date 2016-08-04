Compares two strings in lower-case and returns the difference indicator (see table below) as an integer value.

Syntax
------

``` lua
int utf8.ncasecmp ( string a, string b )
```

### Required Arguments

-   **a:** A string character sequence
-   **b:** A string character sequence

### Returns

Returns an *integer*, which indicates the difference, see the table below for further information.

### Indicators

| Value  | Meaning |
|--------|---------|
| -1     | ``` lua 
          a < b    
          ```      |
| 0      | ``` lua 
          a == b   
          ```      |
| 1      | ``` lua 
          a > b    
          ```      |

Example
-------

<section name="Server" class="server" show="true">
This example shows a simple comparsion of two different strings.

``` lua
local a = "Hello"
local b = "World"
local result = utf8.ncasecmp( a, b )

if result == -1 then
    print( "a < b" ) -- printed
elseif result == 0 then
    print( "a == b" )
elseif result == 1 then
    print( "a > b" )
end
```

</section>
<section name="Server" class="server" show="true">
This example shows how to greet a player, when he write 'hello' into the chat.

``` lua
addEventHandler("onPlayerChat", root,
    function (message, messageType)
        if messageType == 0 and utf8.ncasecmp( message, "hello" ) == 0 then
            outputChatBox( "* Server: Hello!", source, 255, 100, 100 )
        end
    end
)
```

</section>
See Also
--------
