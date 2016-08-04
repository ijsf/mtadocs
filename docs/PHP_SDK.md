You can access the MTA Web Interface from almost any programming language that can request web pages using HTTP POST and encode and decode [JSON](/JSON.md "wikilink"). PHP can do this very easily.

This SDK provides one function *call* that will allow you to call any exported script functions on any server that you have access to.

The download below includes two example pages - one that shows a simple scoreboard, the other that shows the automatic handling of element and resource objects.

If you use this and make any improvements, feel free to send us a copy and we can host it for others to benefit from.

Functions
---------

### call

This function calls an exported function in a specific resource.

**Syntax:** <code lang="php"> $mtaServer = new mta( $hostname, $port, $username, $password ); $resource = $mtaServer-&gt;getResource ( $resourceName ); $returns\[\] = $resource-&gt;call ( “functionName” \[,args...\] );

</syntaxhighlight>
### getInput

This function is for use with web pages that are called by [callRemote](/callRemote.md "wikilink").

**Syntax:** <code lang="php"> inputData\[\] = mta::getInput();

</syntaxhighlight>
### doReturn

Use this function when you want to return data when a page is called with [callRemote](/callRemote.md "wikilink"). You should **NOT** output any other data to the page, e.g. using *echo* as this will cause the return to fail.

**Syntax:** <code lang="php"> mta::doReturn( argument1, argument2 ... argumentN );

</syntaxhighlight>
Examples
--------

<code lang="php"> include( “mta\_sdk.php” ); $mtaServer = new mta(“bastage.net”, 33004); $resource = $mtaServer-&gt;getResource ( “echobot” ); $retn = $resource-&gt;call ( “getThisResource” ); // $retn is an array containing the values the function returned $resourceElement = $retn\[0\]; // the first returned value is the resource $retn = $resource-&gt;call ( “getResourceName”, $resourceElement ); $resourceName = $retn\[0\]; // contains the name of the resource 'echobot'

</syntaxhighlight>
Authentication
--------------

If the server you are accessing requires authentication, you must pass the *http\_username* and *http\_password* variables to your instantiated instance of the mta() class.

**Example:** <code lang="php"> include( “mta\_sdk.php” ); $mtaServer = new mta(“example.com”, 33004, “myUsername”, “myPassword” ); $mtaServer-&gt;getResource(“someResource”)-&gt;call(“someFunction”);

</syntaxhighlight>
A page that can be called by [callRemote](/callRemote.md "wikilink")
--------------------------------------------------------------------

This example just adds two numbers passed to it by a lua script.

**PHP:** (for the page that LUA expects to be at *http://www.example.com/page.php*) <code lang="php"> include( “mta\_sdk.php” ); $input = mta::getInput(); mta::doReturn($input\[0\] + $input\[1\]);

</syntaxhighlight>
**LUA:** <code lang="lua"> -- result is called when the function returns function result(sum)

`   outputChatBox(sum)`

end function addNumbers(number1, number2)

`   callRemote ( `“[`http://www.example.com/page.php`](http://www.example.com/page.php)”`, result, number1, number2 )`

end addNumbers ( 123, 456 ) -- call the function

</syntaxhighlight>
Caveats
-------

-   This only works with PHP 5.0 and above.
-   You cannot currently compare two Element instances that you expect to be identical - you need to do a “deep compare”, comparing the “id” fields.

Download
--------

### Node for version 0.4

On line 80 in mta\_sdk.php you will find the string: <code lang="php"> echo $json\_output;

</syntaxhighlight>
Replace that one with: <code lang="php"> //echo $json\_output;

</syntaxhighlight>
Or remove it completly!

-   [Download Version 0.4](http://code.opencoding.net/mta/mtaphpsdk_0.4.zip) - Renamed *public function mta(..)* to *public function \_\_construct(..)*.
-   [Download Version 0.3](http://code.opencoding.net/mta/mtaphpsdk_0.3_fix.zip) - Neater syntax, support functions for [callRemote](/callRemote.md "wikilink") (fix version makes call work with args).
-   [Download Version 0.2](http://misc.opencoding.net/mta/mtaphpsdk_0.2.zip) - *Deprecated - Syntax differs from examples shown above.* - Adds authentication support.
-   [Download Version 0.1](http://misc.opencoding.net/mta/mtaphpsdk_0.1.zip) - *Deprecated - Syntax differs from examples shown above.*
