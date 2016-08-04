A local variable only exists within the scope it is declared. The scope is the 'level' the variable is visible for the script, containing the value that was assigned to it.

Usage
-----

You should use local variables anytime it is possible, when you don't need to access them globally. This saves you from having troubles with duplicate variable names. Plus, access to local variables is faster.

It is thus also good practice to declare as local any variables that are to exist in any scope within a script file, by declaring it using *local* outside any blocks. The main reason to make a variable global in a resource is when it must be accessed by more than one script file in the resource. Since all script files within a resource share the same global environment, it makes sense to use a global variable here.

Examples
--------

``` lua
function showMoney(source)
    local playermoney = getPlayerMoney ( source )
    outputChatBox(playermoney)
end
```

The *playermoney* variable only exists within the 'showMoney' function.

``` lua
local showHealth = true

outputChatBox("This is your status:", player)
if showHealth == true then
    local health = getElementHealth(player)
    outputChatBox("Health: "..tostring(health), player)
end
```

The *health* variable only exists within the *if*-condition block, that is between the 'then' and the 'end'.

See also
--------

[Programming in Lua: 4.2 Local Variables and Blocks](http://www.lua.org/pil/4.2.html)

[Category:Scripting Concepts](/docs/category:scripting_concepts.md "wikilink")
