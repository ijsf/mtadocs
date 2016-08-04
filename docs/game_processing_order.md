[left|caption](/docs/File:Mta_game_proccess.png.md "wikilink")

Game processing order
---------------------

Here is an overview to show the order in which things get done during an average frame of playing MTA.

The [onClientPreRender](/docs/onClientPreRender.md "wikilink") event is triggered after GTA updates the world, and is the ideal place to do dxDraws that are in some way attached to world elements.

The [onClientHUDRender](/docs/onClientHUDRender.md "wikilink") event is triggered before GTA renders the in-game HUD, so it the best place to apply any full screen effects that you want 'behind' the HUD.
