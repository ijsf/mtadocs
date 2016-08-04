The visibility system for markers and blips works by the following rule: if something is visible to a certain element, it is also visible to all of that element's children. Also, everything is visible to the root element by default.

This means that if you want to make e.g. a blip only visible for a few specific players, you need to do two things:

-   Make the blip invisible to the root element, using [setElementVisibleTo](/docs/setElementVisibleTo.md "wikilink"). The blip is now hidden for all players.
-   Make the blip visible again for the desired players.

The same things go for markers.
