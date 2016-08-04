Currently we sync pretty much everything to everyone. We do reduce the quality of the sync somewhat for distant players, but often this isn't relevant.

Here's a proposed solution someone might like to implement to greatly reduce the bandwidth and CPU usage of servers and clients, when servers are configured to support it.

Solution
--------

-   Add the concept of 'sync worlds' (need a better name).
-   These can work alongside dimensions.
-   Each dimension is in exactly one sync world (there's one by default that all dimensions are in).
-   Players in a sync world receive updates from all the elements that change in that sync world.
-   Elements not in the sync world the player is in aren't synced.
-   When a player switches between two sync worlds, all the elements that have been modified since they were last in that sync world are sent to that client.
-   During the 'resync', a loading screen or indicator is shown.
-   The default behaviour would not use this new feature.

Technically
-----------

-   Add a list that stores 'sync world id' and a timestamp to the player class. This stores the last time a player was sent information about an element in that particular sync world.
-   Add a timestamp to each element that stores the last time that element was updated
-   When we modify an element, update the timestamp
-   Need to consider the variety of ways that elements are synced - keysync, packets, RPC etc.
-   Add a function, e.g. 'setDimensionSyncWorld' to specify the sync world a dimension belongs in.
-   Need to bear in mind that the relevant client-side events should be triggered
-   Need to consider elements that are deleted? Maybe keep a per-sync world list of deleted element ids along with timestamps. Or just delete them on every client? Or something else.

[Category:Proposal](/docs/category:proposal.md "wikilink")
