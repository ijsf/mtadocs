This is a scripting tutorial teaches you the basics about how to start using an Object-Oriented developing interface with Lua. Originally created by [novo](http://forum.mtasa.com/memberlist.php?mode=viewprofile&u=53356) @adam.mta. - [Forum topic](http://forum.mtasa.com/viewtopic.php?f=148&t=84365).

Glossary
--------

-   environment: either a table or an array containing values.
-   self: predefined variable referring to the environment within which we are executing the code.

Initialising
------------

There is a basic and simple predefined variables we should recognize and know: **[self](/docs/#glossary.md "wikilink")**.

### Our first environment

``` lua
local array = {}
function array:example (argument)
    return "Hello" .. argument
end

-- The above is syntactic sugar for:
function array.example(self, argument)
    return "Hello" .. argument
end
```

What we do upon above is defining a *local* environment and then declaring the function **example** as part of it. So how do we call *example*? This is how:

``` lua
array:example(", world!")

-- The above is syntactic sugar for the
-- following line of code. This makes it
-- easier and faster to use OOP in Lua.
array.example(array, ", world!")
```

We're able to call a function using two ways: "**:**" and "**.**". As you can see on the example above, if we use a dot we're directly accessing the function. We need to manually send the *self* value . But if use a colon, *self* will be the environment the function is under, i.e. **array**. We can send the self value in case we want a function to override the object, read ahead to [advanced examples](/docs/#advanced_examples.md "wikilink") for more information about this.

### Variables

``` lua
local array = {text = "none"}
function array:setKey (key, value)
    self[key] = value
end
function array:getKey (key)
    return self[key]
end

array:getKey("text") -- returns "none"
array:setKey("text", "something") -- sets "text"'s value to 'something'
array:getKey("text") -- returns "something"
```

Since we are doing ***array**:setKey(..)*, the “secret” self variable set in both functions are set to **array**. This means that **self\[key\] = value** is actually setting **array\[key\] = value**.

Metatables
----------

Content's provenance: [NovaFusion](http://nova-fusion.com/2011/06/30/lua-metatables-tutorial/)

------------------------------------------------------------------------

Knowledge of the usage of metatables will allow you to create much more powerful scripts. Every table can have a metatable attached to it. A metatable is a table that can change the behaviour of the table it's attached to. Let's see an example.

``` lua
local t = {} -- our normal table
local mt = {} -- our metatable, which contains nothing right now
setmetatable(t, mt) -- set the metatable of *t* to *mt*
getmetatable(t) -- this will return mt
```

As you can see, **getmetatable** and **setmetatable** are the main functions here. This is pretty much self explanatory. A shortened version of this code is this:

``` lua
local t = setmetatable({}, {})
```

The function **setmetatable** returns its first argument, therefore we can use this shorter form.

Now, what do we put in these metatables? Metatables can contain anything, like a regular table, but certain keys that always start with \_\_ (two underscores in a row), such as **\_\_index** and **\_\_newindex** help modify the behaviour of the *target table*. The values corresponding to these keys will usually be functions or other tables. Here's an example:

``` lua
local t = setmetatable({}, {
    __index = function(tab, key)
        if key == "foo" then
            return 0
        else
            return rawget(table, key)
        end
    end
})
```

So as you can see, we assign a function to the **\_\_index** key. Now let's have a look at what this key is all about.

### \_\_index

The most used metatable key is most likely **\_\_index**; it can contain either a function or table.

When you look up a table with a key, regardless of what the key is (t\[4\], t.foo, and t\[“foo”\], for example), and a value hasn't been assigned for that key, Lua will look for an **\_\_index** key in the table's metatable (if it has a metatable). If **\_\_index** contains a table, Lua will look up the key originally used in the table belonging to **\_\_index**. This probably sounds confusing, so here's an example:

``` lua
other = { foo = 3 }
t = setmetatable({hello = "world"}, { __index = other })
t.foo -- 3
t.bar -- nil
t.hello -- "world"
```

If **\_\_index** contains a function, then it's called, with the table that is being looked up and the key used as parameters. By default, this function is “rawget”. As we saw in the code example above the last one, this allows us to use conditionals on the key, and basically anything else that Lua code can do. Therefore, in that example, if the key was equal to the string “foo” we would return 0, otherwise we look up the **table** table with the key that was used; this makes **t** an alias of **table** that returns 0 when the key “foo” is used.

You may be wondering why the table is passed as a first parameter to the **\_\_index** function. This comes in handy if you use the same metatable for multiple tables, supporting code re-use and saving computer resources. We'll see an example of this when we take a look at the **Vector** class.

### \_\_newindex

Next in line is **\_\_newindex**, which is similar to **\_\_index**. Like **\_\_index**, it can contain either a function or table.

When you try to set a value in a table that is not already present, Lua will look for a **\_\_newindex** key in the metatable. It's the same sort of situation as **\_\_index**; if **\_\_newindex** is a table, the key and value will be set in the table specified:

``` lua
other = {}
t = setmetatable({}, { __newindex = other })
t.foo = 3
other.foo -- 3
t.foo -- nil
```

As would be expected, if **\_\_newindex** is a function, it will be called with the table, key, and value passed as parameters:

``` lua
t = setmetatable({}, {
    __newindex = function(t, key, value)
        if type(value) == "number" then
            rawset(t, key, value * value)
        else
            rawset(t, key, value)
        end
    end
})

t.foo = "foo"
print(t.foo) -- "foo"

t.bar = 4
print(t.bar) -- 16

t.la = 10
print(t.la) -- 100
```

When creating a new key in **t**, if the value is a number it will be squared, otherwise it will just be set using the default "\_\_newindex" function, **rawset**.. This introduces us to our friends, **rawget** and **rawset**.

### rawget and rawset

There are times when you need get and set a table's keys without dealing with metatables. [Rawget](http://www.lua.org/manual/5.1/manual.html#pdf-rawget) and [rawset](http://www.lua.org/manual/5.1/manual.html#pdf-rawset) bypass metatables, if you didn't use these when actually getting a value from a table inside a metatable function, an infinite loop will occur. Rawset and rawget do not provide performance enhancements over regular methods, so people don't overuse it to try to gain a performance boost. You may have noticed that the \_\_index arguments are exactly the same as the possible arguments for rawget - this is because rawget/rawset are actually the default metamethods for regular tables.

### Operators

Many of the metatable keys available have to do with operators (as in, **+**, **-**, etc.), allowing you to make tables support the use of operators on them. For example, say we wanted a table to support the multiplication operator (**\***), this is how we would do it:

``` lua
t = setmetatable({}, {
    __mul = function(t, other)
        new = {}
    
        for i = 1, other do
            for _, v in ipairs(t) do table.insert(new, v) end
        end
    
        return new
    end
})
t[1] = "M"
t[2] = "T"
t[3] = "A"
t[4] = 1.4
t = t * 2 -- { "M", "T", "A", 1.4, "M", "T", "A", 1.4 }
```

This allows us to create a new table with the original replicated a certain amount of times using the multiplication operator. The corresponding key for multiplication is **\_\_mul**; unlike **\_\_index** and **\_\_newindex** the keys for operators can only contain functions. The first parameter these functions always receive is the target table, and then the value on the right hand side (except for the unary - which has the key of **\_\_unm**). Here's a list of the supported operators:

-   \_\_add: Addition (+)
-   \_\_sub: Subtraction (-)
-   \_\_mul: Multiplication (\*)
-   \_\_div: Division (/)
-   \_\_mod: Modulos (%)
-   \_\_unm: Unary -, used for negation on numbers
-   \_\_concat: Concatenation (..)
-   \_\_eq: Equality (==)
-   \_\_lt: Less than (&lt;)
-   \_\_le: Less than or equal to (&lt;=)

The operators **&gt;**, **&gt;=** and **~=** do not exist because these can be calculated by flipping the right values. Lua does this:

-   **&gt;**: More than - **not \_\_le**
-   **~=**: Not equal to -- **not \_\_eq**
-   **&gt;=**: More than or equal to - **not \_\_lt**

### \_\_call

Next comes the **\_\_call** key, which allows you to call tables as functions. A code example:

``` lua
t = setmetatable({}, {
    __call = function(t, a, b, c, multiplier)
        return (a + b + c) * multiplier
    end
})

t(1, 2, 3, 4) -- 24
```

The function in \_\_call passes the target table as usual, followed by the arguments we passed to it. **\_\_call** is very useful for many things, it is often used to create new objects.

### \_\_tostring

Last of all is **\_\_tostring**. If implemented, it's used by [tostring](http://www.lua.org/manual/5.1/manual.html#pdf-tostring) to convert a table into a string, most handy when using a function like [print](http://www.lua.org/manual/5.1/manual.html#pdf-print). Normally, when you try to convert a table to a string, you something in the format of “table: 0x<hex-code-here>”, but you can change that using **\_\_tostring**. An example:

``` lua
t = setmetatable({ 1, 2, 3 }, {
    __tostring = function(t)
        sum = 0
        for _, v in pairs(t) do sum = sum + v end
        return "Sum: " .. sum
    end
})

print(t) -- prints out "Sum: 6"
```

### Building the Vector Class

To wrap everything up, we'll write a class encapsulating a 2D vector. It's too large to put here, but you can see the full code at [gist \#1055480](https://gist.github.com/1055480). I've positioned all the stuff to do with metatables first in the file, as that's the most important stuff. (Be warned, this may be a bit confusing if you've never encountered Object-Oriented Programming before.)

``` lua
Vector = {}
Vector.__index = Vector
```

This code sets up the table for the **Vector** class, and sets the **\_\_index** key to point back at itself. Now, what's going on here? You've probably noticed that we've put all the metatable methods inside the **Vector** class. What you're seeing is the simplest way to achieve OOP (Object-Oriented Programming) in Lua. The **Vector** table represents the class, which contains all the functions that instances can use. **Vector.new** (shown below) creates a new instance of this class.

``` lua
function Vector.new(x, y)
  return setmetatable({ x = x or 0, y = y or 0 }, Vector)
end
```

It creates a new table with **x** and **y** properties, and then sets the metatable to the **Vector** class. As we know, **Vector** contains all the metamethods and especially the **\_\_index** key. This means that we can use all the functions we define in **Vector** through this new table. We'll come back to this in a moment.

Another important thing is the last line:

``` lua
setmetatable(Vector, { __call = function(_, ...) return Vector.new(...) end })
```

This means that we can create a new **Vector** instance by either calling **Vector.new** or just **Vector**.

The last important thing that you may not be aware of is the colon syntax. When we define a function with a colon, like this:

``` lua
function t:method(a, b, c)
  -- ...
end
```

What we are really doing is defining this function:

``` lua
function t.method(self, a, b, c)
  -- ...
end
```

This is syntactic sugar to help with OOP. We can then use the colon syntax when calling functions:

``` lua
-- these are the same
t:method(1, 2, 3)
t.method(t, 1, 2, 3)
```

Now, how do we use this **Vector** class? Here's a final example:

``` lua
a = Vector.new(10, 10)
b = Vector(20, 11)
c = a + b
print(a:len()) -- 14.142135623731
print(a) -- (10, 10)
print(c) -- (30, 21)
print(a < c) -- true
print(a == b) -- false
```

Because of the **\_\_index** in **Vector**, we can use all the methods defined in the class through the instances.

Advanced examples
-----------------

Overriding self's value:

``` lua
local array = {text = "none"}
local array2 = {text = "none2"}
function array:setKey (key, value)
    self[key] = value
end
function array:getKey (key)
    return self[key]
end
array.getKey(array2, "text") -- returns "none2"
array.setKey(array2, "text", "something2") -- sets array2's "text" value to 'something2'
array.getKey(array2, "text") -- returns "something"
array:getKey("text") -- returns "none"
array.getKey(array, "text") -- same as above
```

A simple backpacks example:

``` lua
local backpack = {list = {}}
function backpack:create (owner, slots)
    if self.list[owner] then return end -- return false in case this player already owns a backpack
        local new = {
        items = {},
        slots = slots or 100,
        owner = owner
    }
    setmetatable(new.items, 
    {
        __newindex = function(table, key, value) -- this is called once a new value/item is added into the player's table/backpack
            if #table >= new.slots then return end -- return false in case there isn't any free slot left
            return rawset(table, key, value)
        end
    }
    )
    self.list[owner] = new
end

function backpack:addItem (player, item, value)
    if not self.list[player] then return end
    self.list[player][item] = value
end
```

Useful links
============

-   [Official MTA OOP Introduction](/docs/oop_introduction.md "wikilink")
-   [OOP](/docs/oop.md "wikilink")

[Category:Tutorials](/docs/category:tutorials.md "wikilink")
