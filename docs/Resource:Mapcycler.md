The map cycler automatically rotates gamemodes and maps based on a serverside XML listing, end-round map votes, or at random.

Adding gamemode round code
--------------------------

Wherever your gamemode finishes (e.g one team wins, time runs out), add this line:

``` lua
triggerEvent("onRoundFinished", getResourceRootElement(getThisResource()))
```

This will notify the cycler that the round has ended.

List mode
---------

### Cycler configuration XML

The cycler configuration XML will be placed somewhere in the server directory. For now, this is:

` mods/deathmatch/resources/mapcycler/mapcycle.xml`

A gamemode cycle is defined as follows:

``` xml
<cycle type="shuffle">
    <game map="ctf-canals" mode="ctf" rounds="3"/>
    <game map="as-heist" mode="assault" rounds="2"/>
    <game map="i69-laputa" mode="Interstate69" rounds="2"/>
    <game map="sewers" mode="stealth" rounds="2"/>
    <game map="as-sharks" mode="assault" rounds="1"/>
</cycle>
```

Supported list types are **sequential** (the default type, will loop the game list sequentially) and **shuffle** (will loop the list in a random order, without repeating items).

Each game *must* specify a **mode**. **map** is optional (since a gamemode may run without maps), **rounds** defaults to an infinite number of rounds.

### Commands

**nextmap** (outputs the next mode/map)

**nextmode** (same as previous one)

**skipmap** (admin only; cycles to the next mode/map)

Vote mode
---------

The vote mode starts a poll to chose between a set of randomly picked modes with a compatible map (or none, for map-less gamemodes) each.

### Commands

**skipmap** (admin only; cycles to the next mode/map)

Random mode
-----------

The vote mode picks a new mode at random when the rounds finishes.

### Commands

**skipmap** (admin only; cycles to the next mode/map)

[ru:<Resource:Mapcycler>](/ru:Resource:Mapcycler.md "wikilink")
