The client class represents any client that is connected to the server. Therefore, clients are created and destroyed automatically by players' connections or disconnections. They usually are the MTA: SA copy that a [player](/player.md "wikilink") is using (so it has more information about the world), but it can also be the [server console](/Element/Console.md "wikilink").

All client-managing functions operate on both player and server console elements, so the element responsible for a kick can be the server console, for example. However, the server console is protected against some of that functions: it can't get kicked or banned.

The players' clients are also responsible of informing the server about the state of the elements that they're [syncing](/SetElementSyncer.md "wikilink"), so they're essential for accurate sync of peds and vehicles. They also receive data from other clients and the server.

Related scripting functions
---------------------------

[Category:Scripting Concepts](/Category:Scripting_Concepts.md "wikilink")
