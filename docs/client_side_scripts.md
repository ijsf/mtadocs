Client side scripts are scripts that run inside the deathmatch mod client side. This means that the game has access to more information about the game world, but slightly less information about the rest of the players in the game.

This is useful for things that need to be done client side, such as visual effects, creation and manipulation of GUI elements.

How does it work?
-----------------

Client side scripts follow the same pattern as server side scripts. We will try to provide the necessary functionality for client side scripts. Interfacing between a server side and client side script is done by using the same event system as we already have. The server side and client side scripts will need to be in two different files, which are included from the resource (in the metafile) by using a

<script>
tag (and type attribute).

For example:

**meta.xml**

``` xml
<meta>
    <script src="c_gui.lua" type="client" />
    <script src="s_gui.lua" type="server" />
</meta>
```

If you wanted to trigger a client side event from the server, you would first have to register the client side event using [addEvent](/docs/addEvent.md "wikilink"). Then, you can attach a handler to the event as you would in a server side script. Then in the server side script, you'll be able to call [triggerClientEvent](/triggerClientEvent.md "wikilink"), which will trigger the event client side. The same can be done in reverse using [triggerServerEvent](/triggerServerEvent.md "wikilink").

For example:

**Client side**

``` lua
function showObjectBrowser ( id )
    -- code here
end
addEvent( "doShowObjectBrowser", true )
addEventHandler( "doShowObjectBrowser", getRootElement(), showObjectBrowser )
```

**Server side**

``` lua
triggerClientEvent ( somePlayer, "doShowObjectBrowser", getRootElement(), 1034 )
```

[Category:Scripting Concepts](/docs/Category:Scripting_Concepts.md "wikilink") [ru:Client side scripts](/ru:Client_side_scripts.md "wikilink") [it:Script client-side](/it:Script_client-side.md "wikilink") [es:Scripts de Cliente](/es:Scripts_de_Cliente.md "wikilink")
