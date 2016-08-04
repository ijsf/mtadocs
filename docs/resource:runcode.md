**runcode** is a resource that allows dynamic execution of Lua code input from the in-game console, server console or the web interface. This should, in principle, be restricted to server admins.

Console commands
----------------

There are three runcode commands that can be used:

**/run <lua code>**: executes a chunk of server-side code and notifies all players.

**/srun <lua code>**: executes a chunk of server-side code silently (only outputs the command's results to the player who input it).

**/crun <lua code>**: executes a chunk of client-side code for the player who input the command.

Please note that, more often that not, we want to get the value returned by our code, and due to this, the value of the input expression is automatically returned by runcode for all of these commands (this is, “return” is appended to the beginning of the code). While this saves constant typing of the “return” expression, it will produce an error when the code consists in a language construct that does not yield a value (e.g an assignment or a for statement). For these cases, you can input the following statement:

``` lua
loadstring("your code here as a string")()
```

This will load your code chunk as a new function and calls it, so returning its value is possible.

Web interface
-------------

A http interface page is also provided where admins can run server side snippets in a more convenient way. It uses [CodePress](http://codepress.sourceforge.net/) for syntax highlighting, including all available Lua and MTA functions. [ru:<Resource:Runcode>](/docs/ru:Resource:Runcode.md "wikilink")
