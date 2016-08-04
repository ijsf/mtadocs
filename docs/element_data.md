Each [element](/docs/element.md "wikilink") that is loaded is able to have [element data](/docs/element_data.md "wikilink") values attached to it. These are values that can be accessed using a keyword string and directly correspond to the element's attributes in the map file, unless changed via scripting. Element data is a good way to store distributed information you want associated with an element, for example you could use it to associate a score with a player, or a team with a vehicle.

Element data is synchronized between the server and the client. Setting data from any of the two sides will force an update in the other, triggering the corresponding element data change events. This is very useful, as it provides a simple way to keep element properties synced without having to set special events to do it manually. This also means that excessive use of element data to store variables that are not required by both server and client becomes a waste of bandwidth.

Since not all datatypes can be packetized to be transferred, there are some restrictions. The types that cannot be stored as element data are *non-element userdata* (see [MTA Classes](/docs/mta_classes.md "wikilink")), *functions* and *threads*. Also, you may not send tables which contain one or more values of any of these types.

Relevant functions
------------------

-   [setElementData](/docs/setelementdata.md "wikilink"): sets an element data value.
-   [getElementData](/docs/getelementdata.md "wikilink"): retrieves an element data value.
