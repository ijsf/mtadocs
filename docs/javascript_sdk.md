The JavaScript SDK for accessing the MTA Web Interface is currently part of the ajax resource. As such it can only be used in HTML pages hosted on the MTA server as part of a resource. To use it, place the following in the ''

<head>
'' section of your page.

<code lang="lua"> &lt;\* = call(getResourceFromName(“ajax”),“start”, getResourceName(getThisResource()) ) \*&gt;

</syntaxhighlight>
Doing this automatically gives scripts in your page access to all the functions you have exported from your resource, under the same names. For example, if you have exported a “getPlayerCount” function, you can just call this from javascript:

<code lang="javascript"> getPlayerCount ( function ( playerCount ) {

`   alert ( `“`There` `are`”` + playerCount + " players on the server!" );`

} );

</syntaxhighlight>
Notice that this uses an anonymous function as an argument. This function is called when the function returns data. This allows you to continue doing other things in your script while waiting for a response. The arguments for the anonymous function are the same as the returned values from the function you're calling.

You can also manually call a script function using: <code lang="javascript"> callFunction ( “resourceName”, “functionName”, returnFunction, errorFunction \[, arguments... \] );

</syntaxhighlight>
-   **returnFunction:** This is the function that is called when the result of the call is returned. The arguments should be the same as the returned values from the function.
-   **errorFunction:** This function is called when an error occurs. There is a single string argument that specifies what the error is.

Example: <code lang="javascript"> callFunction ( “testResource”, “getPlayerCount”, function ( playerCount ) {

`   alert( `“`There` `are`”` + playerCount + " players on the server!" );`

}, function ( error ) {

`   alert ( `“`Error` `getting` `player` `count:`”` + error );`

});

</syntaxhighlight>
