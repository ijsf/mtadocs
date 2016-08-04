**Lua Predefined variables**

``` lua
_G -- returns a table of all global variables
coroutine -- returns a table containing functions for threads
debug -- returns a table containing debug functions.
math -- returns a table that contains mathematical functions.
string -- returns a table containing functions for strings
table -- returns a table that contains functions for tables
_VERSION -- returns a string of the version of lua in format "Lua 5.1"
self -- used in methods.
```

**MTA Predefined variables**

<section name="Shared" class="both" show="true">
``` lua
exports -- returns a table of resource names containing all export functions
resource -- returns a resource element of the resource the snippet was executed in
resourceRoot -- returns a resource root element of the resource the snippet was executed in
root -- returns the root element of the server
```

</section>
<section name="Client only" class="client" show="true">
``` lua
guiRoot -- returns the root element all GUI elements.
localPlayer -- returns the player element of the local player.
```

</section>
The list of hidden variables, that can be found in functions - handlers:

<section name="Shared" class="both" show="true">
``` lua
source -- The player or element the event was attached to
this -- Element, which was attached function-handler.
eventName -- the name of the event ("onResourceStart", "onPlayerWasted" etc.)
```

</section>
<section name="Server only" class="server" show="true">
``` lua
client -- the client that called the event 
```

</section>
[More details about hidden variables in functions and events](http://wiki.multitheftauto.com/wiki/AddEventHandler)

[Element\_tree](/docs/element_tree.md "wikilink")

List Predefined variables available in the HTTP files:

``` php
requestHeaders -- table, contains all HTTP headlines current page.
form -- table, contains all POST and GET settings, transferred current page.
cookies -- table, contains all COOKIE, transferred current page.
hostname -- string, contains IP or name host, which requested current page.
url -- string, URL current page.
user -- element, account user, which requested current page.
```

[More info about it](http://wiki.multitheftauto.com/wiki/Resource_Web_Access)
