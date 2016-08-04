Many languages can make HTTP POST requests with JSON, C\# can do too. This is C\# SDK for MTA. It allows you to call any HTTP exported functions from resources. The SDK itself is very basic and easy to use. It was mainly created to extend [MTA:Script Editor](/docs/mtase.md "wikilink") functionality. Feel free to modify it however you like but don't remove original author. If you want your changes to be published, please speak to [50p](/docs/user-50p.md "wikilink") on MTA forums [HERE](http://forum.multitheftauto.com/memberlist.php?mode=viewprofile&u=19953)

How to
------

First of all, you have to include your files in your project. Once you've done this, you are ready to use SDK.

1. Add MTA\_SDK.cs and MTA\_LuaArgs.cs to your project file and import the SDK namespace in your file:

    using MTA_SDK;

2. Create instance of MTA class:

    MTA server = new MTA();    //-- default params (for IP and port, respectively) are: "localhost" and 22005

**OR**

    //-- if you don't want to make a call to your local server then you can connect to remote server with the following parameters:
    MTA server = new MTA( "IP", port );

**OR**

    //-- if you get errors about authorization then you should use the account you created on your server 
    //-- (the account that is allowed to visit HTTP sites of your server, preferably admin):
    MTA server = new MTA( "IP", port, "username", "password" );

3. Create instance of MTA\_LuaArgs class to create list of arguments that is passed to the function call:

    MTA_LuaArgs luaArgs = new MTA_LuaArgs( );
    luaArgs.AddValue( "hello" );
    luaArgs.AddValue( "world" );

**OR**

    MTA_LuaArgs luaArgs = new MTA_LuaArgs( "hello", "world" );

4. Call function exported from resource (in meta.xml: <export function="functionName" http="true" />, REMEMBER! http attribute has to be true!):

    string returned = server.CallFunction( "sampleResource", "functionName", luaArgs );

And here is the sample Lua function (functionName) that we're trying to call:

``` lua
function functionName( param1, param2 )
    outputChatBox( "Function called from SDK with args: " .. param1 .. ", " .. param2 );
    return true;
end
```

Download
--------

You can download C\# MTA SDK here:

-   [C\# MTA SDK 1.0](https://drive.google.com/file/d/0B4oc9Fbk4CkUelRrQWVqdmZ3ZDg/view?usp=sharing)

Contact
-------

If you have any questions/suggestions you can contact author on MTA forum or IRC **\#mta** and **\#mtatools** channels hosted on GTANet.com server.

-   [50p](http://forum.multitheftauto.com/memberlist.php?mode=viewprofile&u=19953)
