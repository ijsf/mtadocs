The DirectX scoreboard displays connected players, teams, pings and other data for players ingame. It also has a javascript-enabled web interface, so it can be viewed from a browser. It's created as a replacement for the old [scoreboard](/Resource:OldScoreboard.md "wikilink") resource created by [jbeta](/User:jbeta.md "wikilink").

The biggest difference to the old resource is that it is created fully using MTA's DirectX drawing functions. When you add a column to the scoreboard, it's linked to the element data field of the same name, so if you add the “score” column, element data in the field “score” will be shown for all players and teams.

Download can be found at the [MTA community page](http://community.mtasa.com/index.php?p=resources&s=details&id=419).

Exported functions/events
-------------------------

<section name="Server" class="server" show="true">
### Functions

``` lua
bool scoreboardAddColumn ( string name, [ element forElement = getRootElement(), int width = 70, string friendlyName = name, int priority = slot after "name" column ] )
```

-   **name:** The column name (also the element data name used to get information from).
-   **forElement:** The player to who the column should be added for.
-   **width:** Width of the column in pixels.
-   **friendlyName:** Friendly name (displayed in the scoreboard) of the column.
-   **priority:** The priority slot of the column (1-500). If slot isn't free, the column in that slot will be pushed forward.

``` lua
bool scoreboardRemoveColumn ( string name, [ element forElement = getRootElement() ] )
```

-   **name:** The column name.
-   **forElement:** The player from who the column should be removed.

``` lua
bool scoreboardClearColumns ( [ element forElement = getRootElement() ] )
```

-   **forElement:** The player whose scoreboard's columns should be cleared.

``` lua
bool scoreboardResetColumns ( [ element forElement = getRootElement() ] )
```

-   **forElement:** The player whose scoreboard's columns should be reset (only leaves name and ping).

``` lua
bool scoreboardSetForced ( bool forced, [ element forElement = getRootElement() ] )
```

-   **forced:** Should scoreboard be forced.
-   **forElement:** The player whose scoreboard should be forced.

``` lua
bool scoreboardSetSortBy ( string name, [ bool descending = true, element forElement = getRootElement() ] )
```

-   **name:** The column name. Can also be *nil* making the sorting be disabled.
-   **descending:** Use descending sort.
-   **forElement:** The player whose scoreboard should be sorted.

``` lua
int scoreboardGetColumnPriority ( string name )
```

-   **name:** The column name.

**Returns the column priority (1-500).**

``` lua
bool scoreboardSetColumnPriority ( string name, int priority, [ element forElement = getRootElement() ] )
```

-   **name:** The column name.
-   **priority:** The priority slot of the column (1-500). If slot isn't free, the column in that slot will be pushed forward.
-   **forElement:** The player to who the column should be added for.

``` lua
int scoreboardGetColumnCount ()
```

-   *No arguments.*

**Returns scoreboard column count.**

``` lua
bool scoreboardForceTeamsVisible( bool enabled )
```

-   **enabled:** Should the team header be always visible in the scoreboard (client's setting will be ignored)?

``` lua
bool scoreboardForceTeamsHidden( bool enabled )
```

-   **enabled:** Should the team header be always hidden in the scoreboard (client's setting will be ignored)?

``` lua
bool isPrioritySlotFree( int slot )
```

-   **slot:** The priority slot that should be checked.

**Checks if the specified priority slot is free.**

``` lua
int getNextFreePrioritySlot( [ int startAt = 1 ] )
```

-   **startAt:** At which point should we start looking for free slots.

**Finds the next free priority slot.**

**Note:** These functions used in [scoreboard](/scoreboard.md "wikilink") resource do also work in dxscoreboard.

``` lua
bool addScoreboardColumn ( string columnName, element visibleToElement, int columnPosition, float columnSize )
bool removeScoreboardColumn ( string columnName )
bool setPlayerScoreboardForced ( player thePlayer, bool forced )
bool resetScoreboardColumns ()
```

</section>
<section name="Client" class="client" show="true">
### Functions

``` lua
bool scoreboardAddColumn ( string name, [ int width = 70, string friendlyName = name, int priority = slot after "name" column, function textFunction = nil ] )
```

-   **name:** The column name (also the element data name used to get information from).
-   **width:** Width of the column in pixels.
-   **friendlyName:** Friendly name (displayed in the scoreboard) of the column.
-   **priority:** The priority slot of the column (1-500). If slot isn't free, the column in that slot will be pushed forward.
-   **textFunction:** The text function used to process before displaying the content in the column. For example, this function would replace the "\_"'s in player names with a space, if added to the “name” column.

``` lua
function fixName( playerName )
    return playerName:gsub( "_", " " )
end
```

``` lua
bool scoreboardRemoveColumn ( string name )
```

-   **name:** The column name.

``` lua
bool scoreboardClearColumns ()
```

-   *No arguments.*

``` lua
bool scoreboardResetColumns ()
```

-   *No arguments.*

``` lua
bool scoreboardSetForced ( bool forced )
```

-   **forced:** Should scoreboard be forced.

``` lua
bool scoreboardSetColumnTextFunction ( string name, function textFunction )
```

-   **name:** The column name.
-   **textFunction:** The text function used to process before displaying the content in the column. For example, this function would replace the "\_"'s in player names with a space, if added to the “name” column.

``` lua
function fixName( playerName )
    return playerName:gsub( "_", " " )
end
```

``` lua
bool scoreboardSetSortBy ( string name, [ bool descending = true ] )
```

-   **name:** The column name. Can also be *nil* making the sorting be disabled.
-   **descending:** Use descending sort.

``` lua
int scoreboardGetColumnPriority ( string name )
```

-   **name:** The column name.

**Returns the column priority (1-500).**

``` lua
bool scoreboardSetColumnPriority ( string name, int priority )
```

-   **name:** The column name.
-   **priority:** The priority slot of the column (1-500). If slot isn't free, the column in that slot will be pushed forward.
-   **forElement:** The player to who the column should be added for.

``` lua
int scoreboardGetColumnCount ()
```

-   *No arguments.*

**Returns scoreboard column count.**

``` lua
bool isPrioritySlotFree( int slot )
```

-   **slot:** The priority slot that should be checked.

**Checks if the specified priority slot is free.**

``` lua
int getNextFreePrioritySlot( [ int startAt = 1 ] )
```

-   **startAt:** At which point should we start looking for free slots.

**Finds the next free priority slot.**

``` lua
int, int scoreboardGetTopCornerPosition ()
```

**Returns the absolute position of the scoreboards top corner if it's drawn, *false* otherwise.**

``` lua
int, int scoreboardGetSize ()
```

**Returns the absolute size (width, height) of the scoreboard if it's drawn, *false* otherwise.**

``` lua
table scoreboardGetSelectedRows ()
```

*'Returns a table with all the selected rows (element, which can be either team or player). Can also return an empty table if rows are selected.*

**Note:** These functions used in [scoreboard](/scoreboard.md "wikilink") resource do also work in dxscoreboard.

``` lua
bool setScoreboardForced ( bool forced )
```

### Events

#### onClientPlayerScoreboardClick

``` lua
bool selected, int cursorX, int cursorY
```

-   **selected:** Was the current row selected (*true*) or unselected (*false*).
-   **cursorX:** Absolute X position of the cursor.
-   **cursorY:** Absolute Y position of the cursor.

**Triggered when a player clicks team/player row with the left mouse button.**
**Event *source* is the element was clicked, can be either [player](/player.md "wikilink") or [team](/team.md "wikilink").**

</section>
You can call them from another resource using call()

``` lua
call ( getResourceFromName ( "dxscoreboard" ), "scoreboardAddColumn", "Wanted level" )

-- Note that this syntax is also valid
exports.dxscoreboard:scoreboardAddColumn( "Wanted level" )
```

You can set the scoreboard data with setElementData:

``` lua
-- 3 is inserted in the player's wanted level column, if column
-- called "Wanted level" has been added in the scoreboard
setElementData ( player, "Wanted level", 3 ) 
```

[ru:<Resource:Scoreboard>](/ru:Resource:Scoreboard.md "wikilink")
