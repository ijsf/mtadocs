|            | Operators                                               |
|------------|---------------------------------------------------------|
| Arithmetic | \`+´ , \`-´ , \`\*´ , \`/´ , \`-´ , \`^´                |
| Relational | \`&lt;´ , \`&gt;´ , \`&lt;=´ , \`&gt;=´ , \`==´ , \`~=´ |
| Logical    | \`and´, \`or´, \`not´                                   |
| Misc       | \`..´, \`\#´                                            |

Arithmetic Operators
--------------------

Following table shows all the arithmetic operators supported by Lua language.

| Operator                                                                    |
|-----------------------------------------------------------------------------|
| \`+´ (addition) : Adds two operands Ex: 1 + 5 = 6                           |
| \`-´ (subtraction): Subtracts second operand from the first Ex: 10-30 = -20 |
| \`\*´ (multiplication): Multiply both operands Ex: 5 \* 3 = 15              |
| \`/´ (division): Divide numerator by de-numerator Ex: 8 / 2 = 4             |
| \`^´ (exponentiation): Exponent Operator takes the exponents Ex: 5 ^ 2 = 25 |

### Examples

    local W = 5
    local M = 10
     
    outputChatBox(W + M) -- Addition: 15
    outputChatBox(W - M) -- Subtraction: -5
    outputChatBox(W * M) -- Multiplication: 50
    outputChatBox(W / M) -- Division: 0.5
    outputChatBox(W^2) -- Exponentiation: 25

Relational Operators
--------------------

Relational operators are supplied which return the boolean values true or false.

| Operator                                                        |
|-----------------------------------------------------------------|
| \`==´ (equal to) : Example (5 == 6) false                       |
| \`~=´ (not equal to) : Example (5 ~= 6) true                    |
| \`&lt;´ (less than) : Example (5 &lt; 6 ) true                  |
| \`&gt;´ (greater than) : Example (5 &gt; 6 ) false              |
| \`&lt;=´ (less than or equal to) : Example (5 &lt;= 6 ) true    |
| \`&gt;=´(greater than or equal to) : Example (5 &gt;= 6 ) false |

### Examples

    local W = 5
    local M = 10
     
    -- Example 1 : == Equal to
    if( W == M ) then
       outputChatBox(W.." is equal to "..M )
    else
       outputChatBox(W.." is not equal to "..M )
    end
     
    -- Example 2 : ~= Not equal to
    if( W ~= M ) then
       outputChatBox(W.." is not equal to "..M )
    else
       outputChatBox(W.." is equal to "..M )
    end
     
    -- Example 3 : < less than
    if ( W < M ) then
       outputChatBox(W.." is less than "..M )
    else
       outputChatBox(W.." is not less than "..M )
    end
     
    -- Example 4 : Greater than
    if ( W > M ) then
       outputChatBox(W.." is greater than "..M)
    else
       outputChatBox(W.." is not greater than "..M )
    end
     
    -- Example 5 : <= less than or equal to
    if ( W <= M ) then
       outputChatBox(W.."is either less than or equal to "..M )
    end
     
    -- Example 6 : >= greater than or equal to
    if ( M >= W )
       outputChatBox(M.." is either greater than  or equal to "..W )
    end

Logical Operators
-----------------

Following table shows all the logical operators supported by Lua language.

| Operator                                                                |
|-------------------------------------------------------------------------|
| \`and´: (Called Logical AND operator) Example:(true and false) is false |
| \`or´: (Called Logical OR Operator) Example:(true or false) is true     |
| \`not´: (Called Logical NOT Operator) Example: (not true) is false      |

Misc Operators
--------------

Also there is Miscellaneous operators supported by Lua Language include concatenation and length.

| Operator                                                                     |
|------------------------------------------------------------------------------|
| \`..´ : Concatenates two strings.                                            |
| \`\#´ : An unary operator that return the length of the a string or a table. |

### Examples

    W = "Hello"
    M = "Everybody"
     
    -- Example 1 : Concatenates two strings.
    outputChatBox(W.." "..M) -- Result: Hello Everybody
     
    -- Example 2:
    outputChatBox(#W) -- Result: 5

[Category:Scripting Concepts](/docs/Category:Scripting_Concepts.md "wikilink")
