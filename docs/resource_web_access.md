The Multi Theft Auto Server provides a web interface that resources can use in a variety of ways. This document's purpose is to explain what these ways are and how to go about using them.

Overview
--------

There are two key parts that make up this system. The first is a standard web server that allows web browsers to request pages and files you have in a resource. The second is a system for allowing web browsers to call functions you have exported from your resource.

Pages
-----

### Specifying a file in the meta

You can specify in your resource's meta file that certain files are accessible through the web server. To do this, you add a line: <code lang="xml">

<html src="filename.ext" />
</syntaxhighlight>
You can then access this file from your web browser by visiting: [http://host:port/resourcename/filename.ext](http://host:port/resourcename/filename.ext)
For example, on a locally hosted server using default http port with webmap started: <http://127.0.0.1:22005/webmap/map.htm>

### Binary files

Despite the misleading name, files specified using the html node can be of any type. If they are binary files (like images, zip files) then you need to specify this in the meta file, by adding *raw=“true”* to the *html* node. This means that the files are not preprocessed before being sent to the web browser.

For example: <code lang="xml">

<html src="image.gif" raw="true" />
</syntaxhighlight>
### Parsed files

If a file is not specified in the meta file as “raw”, then it is passed through a pre-processor before it is returned to the client. This pre-processor works much like PHP or ASP, but uses LUA. You can embed standard MTA scripts within HTML pages, controlling the output. Almost all standard MTA functions work, plus a number of special [HTTP Functions](/docs/template-http_functions.md "wikilink"), such as [httpWrite](/docs/httpwrite.md "wikilink"), a function that outputs text to the buffer.

For example: <code lang="html4strict">

<html>
<body>
`       This resource is called <* httpWrite( getResourceName(getThisResource()) ) *>`
`   `

</body>
<html>
</syntaxhighlight>
There is a shorthand (in common with PHP and ASP) for this code, meaning that you can also write the above code as:

<code lang="html4strict">

<html>
<body>
`       This resource is called <* = getResourceName(getThisResource()) *>`
`   `

</body>
<html>
</syntaxhighlight>
Aside from HTTP functions, embedded Lua has access to the following environment variables that contain information about how the page was requested:

-   table **requestHeaders**: This is a table containing all the headers that were requested with the page. You can set returned headers using [httpSetResponseHeader](/docs/httpsetresponseheader.md "wikilink").
-   table **form**: This is a table containing all the form data submitted to the page using HTTP POST combined with any variables passed in the querystring with HTTP GET.
-   table **cookies**: This is a table of all the cookies. You can modify cookies using [httpSetResponseCookie](/docs/httpsetresponsecookie.md "wikilink").
-   string **hostname**: This is a string containing the IP address or hostname that requested the page.
-   string **url**: This is the URL of the page.
-   account **user**: This is the account of the current user.

It's important to note that parsed files are run in a separate virtual machine from the rest of your resource's code. As such, if you want to call a function in your resource's main code, you need to export the function and use the [call](/docs/call.md "wikilink") function from your parsed file.

Calls
-----

You can specify that certain exported functions in your resource are able to be called from the HTTP interface. All the SDKs (listed below) allow you to call these functions from a remote location.

To specify an exported http-accessible function, add the following to your meta.xml file: <code lang="xml"> <export function='functionName' http='true' />

</syntaxhighlight>
You can code your function just as you would any normal function, returning as many values as you want, including tables and resources and most importantly elements. You *cannot* however return other 'userdata' values such as [xmlnodes](/docs/xmlnode.md "wikilink") or functions.

### Protocol

Calls are done by requesting *http://&lt;your IP&gt;:&lt;your port&gt;/&lt;resource\_name&gt;/call/&lt;exported\_function\_name&gt;* using HTTP POST. The body of the request should be a JSON array of the arguments for the function.

The request will return a JSON array of the value(s) returned from the function as the HTTP response.

The server supports HTTP Basic authentication and you can configure access via the ACL and the built-in accounts system.

### Calls from the HTTP web interface

Using calls is probably easiest from the web interface and can be done almost seamlessly.

First, add this to your meta.xml file: <code lang="xml"> <include resource="ajax" />

</syntaxhighlight>
Secondly, add the following to the

<head>
section of the page you want to call from: <code lang="lua"> &lt;\* = exports.ajax:start(getResourceName(getThisResource())) \*&gt;

</syntaxhighlight>
Finally, you can create a javascript block in your page and call your functions almost as if they were local. The only difference is that the calls are aysnchronous - you should specify a callback function as the last argument for your call. This is called when the function returns.

Here's a simple example.

**meta.xml** <code lang="xml"> <meta>

`  `<include resource="ajax" />
`  `

<script src='code.lua' />
<html src='page.htm' default='true' />
`  `<export function='showChatMessage' http='true' />

</meta>

</syntaxhighlight>
**code.lua** <code lang="lua"> function showChatMessage ( message )

`   outputChatBox ( message )`
`   return 5;`

end

</syntaxhighlight>
**page.htm** <code lang="html4strict">

<html>
<head>
`       <* = exports.ajax:start(getResourceName(getThisResource())) *>`
`       `

<script type='text/javascript'>
`           function say() {`
`               var message = document.getElementById('message')`
`               showChatMessage ( message.value, `
`                   function ( number ) {`
`                       // the function has been called and returned something`
`                       message.value = `“`The` `function` `returned`”` + number;`
`                   }`
`               );`
`           }`
`       `

</script>
</head>
<body>
`       `<input type='text' id='message' /><input type='button' value='say' onclick='say();' />
`   `

</body>
</html>
</syntaxhighlight>
You can see (fairly complex) examples of how this can be done in the resources *resourcebrowser*, *resourcemanager* and *webadmin*.

Securing the web interface
--------------------------

The [ACL](/docs/acl.md "wikilink") has a number of rights that can affect what files can be accessed.

SDK
---

There are a number of so-called 'SDKs' available that allow you to interface with the server from other programming languages. With these you could (in theory) write whole gamemodes. In practice this is probably a bad idea, but it is useful for statistics and administration. The PHP SDK is the most developed version. Feel free to modify or create your own SDKs - if you do please send us a copy.

-   [Java SDK](/docs/javasdk.md "wikilink")
-   [Javascript SDK](/docs/javascript_sdk.md "wikilink")
-   [Perl SDK](/docs/perl_sdk.md "wikilink")
-   [PHP SDK](/docs/php_sdk.md "wikilink")
-   [C\# SDK](/docs/csharp_sdk.md "wikilink")

See Also
--------

[callRemote](/docs/callremote.md "wikilink") - Allows game servers to call functions on PHP pages (with the PHP SDK) and on other game servers. [Category:Scripting Concepts](/docs/category-scripting_concepts.md "wikilink") [ru:Resource Web Access](/docs/ru-resource_web_access.md "wikilink") [Category:Tutorials](/docs/category-tutorials.md "wikilink")
