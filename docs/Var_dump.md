<lowercasetitle>var\_dump</lowercasetitle>

This function outputs information about one or more variables using outputConsole().

Syntax
------

``` lua
string/table var_dump( ... )
```

### Arguments

The function can have a variable number of arguments. Those arguments can be of three types:

-   **Modifiers:** A *string* that begins with a "-" (minus) and that is followed by at least another parameter is a modifier. A modifier can change the behaviour of the function. Modifiers don't have to be the first argument, they always work on all arguments after it (see examples).
-   **Names:** A *string* that is followed by at least another parameter and isn't preceeded by another *string* (that is not a modifier), is a name. A name is output before the variable output, to make it recognizable (basicially a description of the variable that is being output, e.g. the name).
-   **Values:** Any value that is not one of the two above will generate an output with information about the variable:
    -   For *strings*: string(*lengthOfString*) "*value*"
    -   For *userdata*: userdata(*MTA element type*) "*value*"
    -   For *tables*: table(*numerOfElements*) "*value*"
        -   If the table contains any elements, they will also be output if the appropriate modifiers are set. This will always be in the form \[*key*\] =&gt; *value*, while *key* and *value* are formatted by var\_dump.

### Modifiers

-   **v** (verbose): Dumps more data than usual (for now it outputs whole tables including subtables)
-   **n** (normal): Switches back into 'normal' non-verbose mode.
-   **s** (silent): With this activated, it outputs nothing at all, however it still returns the output, so you can use it yourself (also used internally for recursion).
-   **u** (unnamed): Don't use names. Every *string* that is not a modifier will be output as a value, not a decription.
-   **d\[number\]** (depth): Output nested tables up to this depth (e.g. “d1” means output all values of the initial table, but not the values of the values, if they are also tables).

### Returns

Returns a string with all the output in one line and a table with several lines of output.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
<code lang="lua"> -- modifiers: v - verbose (all subtables), n - normal, s - silent (no output), dx - up to depth x, u - unnamed function var\_dump(...)

`   -- default options`
`   local verbose = false`
`   local firstLevel = true`
`   local outputDirectly = true`
`   local noNames = false`
`   local indentation = "\t\t\t\t\t\t"`
`   local depth = nil`

`   local name = nil`
`   local output = {}`
`   for k,v in ipairs(arg) do`
`       -- check for modifiers`
`       if type(v) == `“`string`”` and k < #arg and v:sub(1,1) == "-" then`
`           local modifiers = v:sub(2)`
`           if modifiers:find(`“`v`”`) ~= nil then`
`               verbose = true`
`           end`
`           if modifiers:find(`“`s`”`) ~= nil then`
`               outputDirectly = false`
`           end`
`           if modifiers:find(`“`n`”`) ~= nil then`
`               verbose = false`
`           end`
`           if modifiers:find(`“`u`”`) ~= nil then`
`               noNames = true`
`           end`
`           local s,e = modifiers:find(`“`d%d+`”`)`
`           if s ~= nil then`
`               depth = tonumber(string.sub(modifiers,s+1,e))`
`           end`
`       -- set name if appropriate`
`       elseif type(v) == `“`string`”` and k < #arg and name == nil and not noNames then`
`           name = v`
`       else`
`           if name ~= nil then`
`               name = ""..name..": "`
`           else`
`               name = ""`
`           end`

`           local o = ""`
`           if type(v) == `“`string`”` then`
`               table.insert(output,name..type(v).."("..v:len()..") \""..v.."\"")`
`           elseif type(v) == `“`userdata`”` then`
`               local elementType = `“`no` `valid` `MTA` `element`”
`               if isElement(v) then`
`                   elementType = getElementType(v)`
`               end`
`               table.insert(output,name..type(v).."("..elementType..") \""..tostring(v).."\"")`
`           elseif type(v) == `“`table`”` then`
`               local count = 0`
`               for key,value in pairs(v) do`
`                   count = count + 1`
`               end`
`               table.insert(output,name..type(v).."("..count..") \""..tostring(v).."\"")`
`               if verbose and count > 0 and (depth == nil or depth > 0) then`
`                   table.insert(output,"\t{")`
`                   for key,value in pairs(v) do`
`                       -- calls itself, so be careful when you change anything`
`                       local newModifiers = "-s"`
`                       if depth == nil then`
`                           newModifiers = "-sv"`
`                       elseif  depth > 1 then`
`                           local newDepth = depth - 1`
`                           newModifiers = "-svd"..newDepth`
`                       end`
`                       local keyString, keyTable = var_dump(newModifiers,key)`
`                       local valueString, valueTable = var_dump(newModifiers,value)`
`                       `
`                       if #keyTable == 1 and #valueTable == 1 then`
`                           table.insert(output,indentation.."["..keyString.."]\t=>\t"..valueString)`
`                       elseif #keyTable == 1 then`
`                           table.insert(output,indentation.."["..keyString.."]\t=>")`
`                           for k,v in ipairs(valueTable) do`
`                               table.insert(output,indentation..v)`
`                           end`
`                       elseif #valueTable == 1 then`
`                           for k,v in ipairs(keyTable) do`
`                               if k == 1 then`
`                                   table.insert(output,indentation.."["..v)`
`                               elseif k == #keyTable then`
`                                   table.insert(output,indentation..v.."]")`
`                               else`
`                                   table.insert(output,indentation..v)`
`                               end`
`                           end`
`                           table.insert(output,indentation.."\t=>\t"..valueString)`
`                       else`
`                           for k,v in ipairs(keyTable) do`
`                               if k == 1 then`
`                                   table.insert(output,indentation.."["..v)`
`                               elseif k == #keyTable then`
`                                   table.insert(output,indentation..v.."]")`
`                               else`
`                                   table.insert(output,indentation..v)`
`                               end`
`                           end`
`                           for k,v in ipairs(valueTable) do`
`                               if k == 1 then`
`                                   table.insert(output,indentation.." => "..v)`
`                               else`
`                                   table.insert(output,indentation..v)`
`                               end`
`                           end`
`                       end`
`                   end`
`                   table.insert(output,"\t}")`
`               end`
`           else`
`               table.insert(output,name..type(v).." \""..tostring(v).."\"")`
`           end`
`           name = nil`
`       end`
`   end`
`   local string = ""`
`   for k,v in ipairs(output) do`
`       if outputDirectly then`
`           outputConsole(v)`
`       end`
`       string = string..v`
`   end`
`   return string, output`

end

</syntaxhighlight>
</section>
Example
-------

<section name="Serverside Example" class="server" show="true">
Get a table of all players on the server (if there are 4 players). <code lang="lua"> var\_dump(getElementsByType(“player”))

</syntaxhighlight>
Output:

    table(4) "table: 02998058"

With 'verbose' modifier.

    var_dump("-v",getElementsByType("player"))

    table(1) "table: 043C6900"
     {
          [number "1"] => userdata(player) "userdata: 00000134"
     }

Now another table we created before (please note that the table 'test2' is both key and value in this example):

    test = {hello="test"}
    test2 = {"haha","naja"}
    test[test2] = test2
    var_dump("-v",getElementsByType("player"),test)

    table(1) "table: 020B7838"
     {
          [number "1"] => userdata(player) "userdata: 00000134"
     }
    table(2) "table: 021770A0"
     {
          [string(5) "hello"] => string(4) "test"
          [table(2) "table: 02313070"
           {
                [number "1"] => string(4) "haha"
                [number "2"] => string(4) "naja"
           }]
           => table(2) "table: 02313070"
           {
                [number "1"] => string(4) "haha"
                [number "2"] => string(4) "naja"
           }
     }

The same as before, but now with a modifier to output the second table 'normal':

    test = {hello="test"}
    test2 = {"haha","naja"}
    test[test2] = test2
    var_dump("-v",getElementsByType("player"),"-n",test)

    table(1) "table: 01BB9030"
     {
          [number "1"] => userdata(player) "userdata: 00000134"
     }
    table(2) "table: 0223B2D8"

The same as before, but now with a modifier to output the second table only to depth 1 (the verbose is still active from the first argument):

    test = {hello="test"}
    test2 = {"haha","naja"}
    test[test2] = test2
    var_dump("-v",getElementsByType("player"),"-d1",test)

    table(1) "table: 029BE6E8"
     {
          [number "1"] => userdata(player) "userdata: 00000134"
     }
    table(2) "table: 01E2CDF8"
     {
          [string(5) "hello"] => string(4) "test"
          [table(2) "table: 021C6378"] => table(2) "table: 021C6378"
     }

The same as before, but now with names to make clear which output belongs to which variable (of course in this small example, it's not really needed):

    test = {hello="test"}
    test2 = {"haha","naja"}
    test[test2] = test2
    var_dump("-v","players",getElementsByType("player"),"-d1","test tables",test)

    players: table(1) "table: 0219F4D0"
     {
          [number "1"] => userdata(player) "userdata: 00000134"
     }
    test tables: table(2) "table: 0219DB20"
     {
          [string(5) "hello"] => string(4) "test"
          [table(2) "table: 01B68048"] => table(2) "table: 01B68048"
     }

The same as before, but now 'unnamed', meaning all values that are not modifiers will be output as values. However, the last two arguments were also removed, which leaves the last modifier as last argument, which will output the modifier as a normal value:

    var_dump("-u","players",getElementsByType("player"),"-d1")

    string(7) "players"
    table(1) "table: 028B8A10"
    string(3) "-d1"

</section>
See Also
--------
