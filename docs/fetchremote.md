This function allows you to post and receive data from HTTP servers. The calls are asynchronous so you do not get an immediate result from the call, instead a callback function you specify is called when the download completes.

In the case when the call fails, a string containing “ERROR” followed by an integer containing the error reason will be passed to the callback function. The reason for failure will be similar to errors found with websites - file not found, server not found and timeouts.

If you are using fetchRemote to connect to a PHP script, you can use *file\_get\_contents(“php://input”)* to read the **postData** sent from this function.

Syntax
------

``` lua
bool fetchRemote ( string URL[, int connectionAttempts = 10 ], function callbackFunction, [ string postData = "", bool postIsBinary = false, [ arguments... ] ] )
```

### Required Arguments

-   **URL:** A full URL in the format *http://hostname/path/file.ext*. A port can be specified with a colon followed by a port number appended to the hostname.
-   **callbackFunction:** This is the function that should receive the data returned from the remote server. The callback argument list should be:
    -   ***responseData*** - A string containing the remote response or “ERROR” if there was a problem
    -   ***errno*** - A number containing the error number or zero if there was no error. A list of possible error values are:

<div style="padding-left:19px;">
-   ***arguments...*** - The arguments that were passed into fetchRemote

</div>
### Optional Arguments

-   **connectionAttempts:** Number of times to retry if the remote host does not respond. *In the case of a non-responding remote server, each connection attempt will timeout after 10 seconds. Therefore, the default setting of 10 connection attempts means it will be 100 seconds before your script gets a callback about the error. Reducing this value to 2 for example, will decrease that period to 20 seconds*
-   **postData:** A string specifying any data you want to send to the remote HTTP server.
-   **postIsBinary :** A boolean specifying if the data is text, or binary.
-   **arguments:** Any arguments you may want to pass to the callback.

### Returns

Returns *true* if the arguments are correct, *false* otherwise.

Example
-------

This example shows you how you can fetch an image from a web page, and transfer it to a particular client:

<section name="Server" class="server" show="true">
``` lua

function startImageDownload( playerToReceive )
    fetchRemote ( "http://www.example.com/image.jpg", myCallback, "", false, playerToReceive )
end

function myCallback( responseData, errno, playerToReceive )
    if errno == 0 then
        triggerClientEvent( playerToReceive, "onClientGotImage", resourceRoot, responseData )
    end
end
```

</section>
<section name="Client" class="client" show="true">
``` lua
addEvent( "onClientGotImage", true )
addEventHandler( "onClientGotImage", resourceRoot,
    function( pixels )
        if myTexture then
            destroyElement( myTexture )
        end
        myTexture = dxCreateTexture( pixels )
    end
)

addEventHandler("onClientRender", root,
    function()
        if myTexture then
            local w,h = dxGetMaterialSize( myTexture )
            dxDrawImage( 200, 100, w, h, myTexture )
        end
    end
)
```

</section>
Requirements
------------

Changelog
---------

See Also
--------
