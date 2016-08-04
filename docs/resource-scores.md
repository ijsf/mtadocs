This resource provides kills, deaths, suicides, kill/death ratio and alive/dead status columns.

Usage
-----

Include “scores” in your resource (this also includes the scoreboard, so you don't need to do it). From your script, select the columns that you want enabled through the settings system, and then force an update (this is necessary since we don't have settings registry events yet).

Example:

``` lua
set("scores.kills", true) --enable kills column
set("scores.deaths", true) --enable deaths column
set("scores.self", false) --disable self-kills column
--...
call(getResourceFromName("scores"), "updateActiveColumns")
```

Keep in consideration that the columns do not have set defaults, so you should explicitly enable or disable all of them.

Columns
-------

**kills**

**deaths**

**self**

**ratio**

**status**

Exported functions
------------------

### Server

``` lua
bool updateActiveColumns ( )
```

Changes the active scoreboard columns according to the resource's current settings.

[ru:<Resource:Scores>](/docs/ru-resource-scores.md "wikilink")
