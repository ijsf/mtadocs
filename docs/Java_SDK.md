This SDK allows you to call exported MTA functions from Java over HTTP.

Getting Started
---------------

To use it, you need to make sure you need to have the following packages:

-   *com.multitheftauto*
-   *org.json.simple*
-   *org.json.simple.parser*

These are all included in the zip file below.

To get started, import com.multitheftauto.MTARPC.

Syntax
------

This class has one public static function, *callFunction*. The syntax is as follows: <code lang="java5"> Object\[\] callFunction ( String serverHTTPAddress, String resourceName, String functionName, Object\[\] args )

</syntaxhighlight>
-   **serverHTTPAddress:** The server's HTTP address, in the form hostname:port (without “<http://>” prefixed)
-   **resourceName:** The name of the resource that has exported the function you want to call
-   **functionName:** The name of the function you want to call
-   **args:** An array of arguments you wish to pass. Most basic types are accepted - String, Integer, Double, Boolean, null etc, as well as the special classes com.multitheftauto.Element and com.multitheftauto.Resource.

Examples
--------

This tests the resource functions exported from the 'echobot' resource: <code lang="java5"> Object\[\] ret = MTARPC.callFunction ( SERVER\_HTTP\_ADDRESS, “echobot”, “getThisResource”, null ); Resource resource = (Resource)ret\[0\]; Object\[\] arguments = {resource}; ret = MTARPC.callFunction ( SERVER\_HTTP\_ADDRESS, “echobot”, “getResourceName”, arguments ); String resourceName = (String)ret\[0\]; System.out.println(“Resource name:” + resourceName );

</syntaxhighlight>
This example tests the element functions exported from the 'echobot' resource: <code lang="java5"> // call getRootElement Object\[\] ret = MTARPC.callFunction ( SERVER\_HTTP\_ADDRESS, “echobot”, “getRootElement”, null ); Element rootElement = (Element)ret\[0\];

// call getElementType Object\[\] arguments = {rootElement}; ret = MTARPC.callFunction ( SERVER\_HTTP\_ADDRESS, “echobot”, “getElementType”, arguments ); String rootElementType = (String)ret\[0\];

System.out.println(“Root element type:” + rootElementType );

</syntaxhighlight>
More complex example
--------------------

[Image:Mta java sdk example.png](/Image:Mta_java_sdk_example.png.md "wikilink")

The zip file contains an example program (MTAJavaTest.java) that implements a console that allows you to see events on a server and chat to the players there. This allows you to see how you can handle multiple returns.

Caveats
-------

-   You cannot currently compare two Resource or Element objects that you expect to be identical - you need to do a “deep compare”, comparing either the “id” fields or the “name” fields.

Download
--------

-   [Download Version 0.1](http://misc.opencoding.net/mta/mtajavasdk_0.1.zip)

[Category:Scripting Concepts](/Category:Scripting_Concepts.md "wikilink")
