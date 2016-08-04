This function allows you to call functions that have been exported with HTTP access by other MTA servers. The calls are asynchronous so you do not get an immediate result from the call, instead a callback function you specify is called when the call returns.

You can also use this function to access a standard web page on a server you own by specifying the URL. The arguments you specify to callRemote are passed to the web page using HTTP POST as a [JSON](/docs/JSON.md "wikilink") array. This will always have an array as the root element. The page must return a JSON formated \*array\* in the page's body with the results of the call (or an empty array if there are no results).

You can use the [PHP SDK](/docs/PHP_SDK.md "wikilink") to create PHP pages that can be called by this function. See the PHP SDK page for an example.

In addition, it is possible to use this function to get information about a resource in the MTA community, besides other things. Check out the [Community Resources](/docs/Community_Resources.md "wikilink") article.

In the case when the call fails, a string containing “ERROR” followed by an integer containing the error reason will be passed to the callback function. The reason for failure will be similar to errors found with websites - file not found, server not found and timeouts.

Syntax
------

``` lua
bool callRemote ( string host[, int connectionAttempts = 10 ], string resourceName, string functionName, callback callbackFunction, [ arguments... ] )
```

**OR**

``` lua
bool callRemote ( string URL[, int connectionAttempts = 10 ], callback callbackFunction, [ arguments... ] )
```

### Required Arguments

-   **host:** This is a host name - including the **HTTP** port - of the server you wish to connect to.
-   **resourceName:** This is a name of the resource that contains the exported function you want to call.
-   **functionName:** This is a string with the name of the function which you want to call.
-   **URL:** A full URL in the format *http://hostname/path/file.ext*. A port can be specified with a colon followed by a port number appended to the hostname.
-   **callbackFunction:** This is the function that should receive the data returned from the remote function call. The argument list should match the format of the data returned. The callback function will be passed a string containing “ERROR” followed by an integer indicating the error code when an error occurs calling the function. A list of error codes [can be found here](/docs/Template:Error_codes_for_callRemote_and_fetchRemote.md "wikilink").

### Optional Arguments

-   **arguments:** Any arguments you may want to pass to the function when it is called. Any number of arguments of can be specified, each being passed to the designated function. Most data types can be passed, including tables. The only values that cannot be passed are 'userdata' values such as xmlnodes - elements and resources can be passed though may be misinterpreted on other game servers (or cause warnings).

### Returns

Returns *true* if the function has been called, *false* otherwise.

Example
-------

This example shows you how you can call a PHP page from a lua script. It just adds two numbers passed to it by the script and outputs these in the chat box.

**PHP:** (for the page that LUA expects to be at *http://www.example.com/page.php*)

``` php
include( "mta_sdk.php" );
$input = mta::getInput();
mta::doReturn($input[0] + $input[1]);
```

**LUA:**

``` lua
-- result is called when the function returns
function result(sum)
    if sum ~= "ERROR" then
        outputChatBox(sum)
    end
end
function addNumbers(number1, number2)
    callRemote ( "http://www.example.com/page.php", result, number1, number2 )
end 
addNumbers ( 123, 456 ) -- call the function
```

<hr>
**Example 2:** This example shows how you can join up multiple servers so they can share chat messages.

**Meta.xml** First, add *outputChatBoxRemote* as an HTTP exported function in your resource's meta.xml:

``` xml
<export function="outputChatBoxRemote" http="true" />
```

**LUA:** Next, add this to a server-side script in your resource:

``` lua
-- Remote function set with callRemote 'functionName' argument
-- Called from/on remote servers
function outputChatBoxRemote ( playerName, message, type, serverport )
    outputChatBox ( "From " .. playerName .. " on " .. serverport .. ": " .. message )
    return "hello sailor"
end

-- Callback set with callRemote 'callbackFunction' argument
-- Called on the local server when callRemote has completed successfully or with errors
function finishedCallback( responseData, errno )
    responseData = tostring(responseData)
    if responseData == "ERROR" then
        outputDebugString( "callRemote: ERROR #" .. errno )
    elseif responseData ~= "hello sailor" then
        outputDebugString( "callRemote: Unexpected reply: " .. responseData  )
    else
        -- callRemote completed successfully
    end
end

function playerChat ( message, type )
    callRemote ( "play.mtabeta.com:33004", getResourceName(getThisResource()), "outputChatBoxRemote", finishedCallback, getPlayerName(source), message, type, getServerPort() )
    callRemote ( "play.mtabeta.com:33005", getResourceName(getThisResource()), "outputChatBoxRemote", finishedCallback, getPlayerName(source), message, type, getServerPort() )
    callRemote ( "play.mtabeta.com:33006", getResourceName(getThisResource()), "outputChatBoxRemote", finishedCallback, getPlayerName(source), message, type, getServerPort() )
end
addEventHandler ( "onPlayerChat", getRootElement(), playerChat )
```

**ACL:** Then, modify the ACL on each sending server to allow access to callRemote:

``` xml
<group name="OutRPCGroup">
    <acl name="OutRPC" />
    <object name="resource.examplechat" />
</group>
<acl name="OutRPC">
    <right name="function.callRemote" access="true" />
</acl>
```

**ACL \#2:** Finally, modify the ACL on each receiving server to allow guest http communication with your resource:

``` xml
<group name="InRPCGroup">
    <acl name="InRPC" />
    <object name="user.http_guest" />
</group>
<acl name="InRPC">
    <right name="resource.examplechat.http" access="true" />
</acl>
```

Changelog
---------

See Also
--------
