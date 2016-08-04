This script manages any kind of poll with multiple options. **votemap**, **votekick**, **votekill** and **voteban** are built in.

Built-in polls
--------------

**votemap** (starts a vote between a random list of up to 9 maps compatible with the current gamemode, if one is running)

**votemap gamemode** (starts a vote between a random list of up to 9 maps compatible with the specified gamemode)

**votemap gamemode map** (starts a vote to launch the specified gamemode with the specified map)

**votemap map** (starts a vote to change to another map for the current gamemode, if one is running)

**votemode** (starts a vote between a random list of up to 9 gamemodes. once the vote is done and a new gamemode is picked, automatically starts 'votemap gamemode')

**votekick player** (starts a vote to kick the specified player)

**votekill player** (starts a vote to kill the specified player)

**voteban player** (starts a vote to ban the specified player)

Serverside functions
--------------------

### startPoll

``` lua
bool, int startPoll ( table pollData )
```

Creates a poll. Returns *true* if the poll was created successfully, *false* and an error code otherwise (see the source for error codes).

-   **pollData** is a table containing poll settings and an array of *at least two* options. Each option comes in the form:

``` lua
{
string optionName,
string eventToTrigger,
[element triggerFrom = getRootElement()],
default = [bool isDefaultOption = false],
var argument1,
var argument2,
...
}
```

The chosen option will trigger eventToTrigger from the triggerFrom element with *arguments...* as parameters when the poll ends.

If there's not enough votes, the default option will be executed if there's one.

Example:

``` lua
local playerToKill = getRandomPlayer()
local notEnoughVotesMessage = "Not enough votes to kill "..getPlayerName(playerToKill).."."
startPoll {
   --start settings (dictionary part)
   title="Kill "..getPlayerName(playerToKill).."?",
   percentage=75,
   timeout=30,
   allowchange=false,
   maxnominations=3,
   visibleTo=getRootElement(),
   --start options (array part)
   [1]={"Yes", "doKillPlayer", playerToKill},
   [2]={"No", "doOutputChatBox", notEnoughVotesMessage, getRootElement(), vR, vG, vB; default=true},
}
```

-   **title** (required): the poll title which will be seen by clients on the manager GUI
-   **percentage** (optional, defaults to default.percentage): percentage needed for an option to pass
-   **timeout** (optional, defaults to default.timeout): poll timeout in seconds
-   **allowchange** (optional, defaults to default.allowchange): specifies if changing your vote is allowed
-   **maxnominations** (optional, defaults to default.maxnominations): specifies the max number of nominations in case there's a draw
-   **visibleTo** (optional, defaults to [getRootElement](/getRootElement.md "wikilink")()): a table or players that will be able to see the poll, OR an element that contains the players.

If it is root, new players joining the server will be able to vote.

*voteconfig.xml* defaults will be used for missing optional settings.

### stopPoll

``` lua
bool, int stopPoll ( )
```

Stops the running poll. Returns *true* if the current poll was stopped successfully, *false* and an error code otherwise.

### voteMap

``` lua
bool, int voteMap ( string mapName )
```

Starts a votemap. Returns *true* if it was successfully started, *false* and an error code otherwise.

### voteBetweenMaps

``` lua
 )
```

Starts a poll to choose a map. Returns *true* if it was successfully started, *false* and an error code otherwise.

### voteKick

``` lua
bool, int voteKick ( player thePlayer )
```

Starts a votekick. Returns *true* if it was successfully started, *false* and an error code otherwise.

### voteKill

``` lua
bool, int voteKill ( player thePlayer )
```

Starts a votekill. Returns *true* if it was successfully started, *false* and an error code otherwise.

### voteBan

``` lua
bool, int voteBan ( player thePlayer )
```

Starts a voteban. Returns *true* if it was successfully started, *false* and an error code otherwise.

Serverside events
-----------------

### onPollStarting

``` lua
void onPollStarting ( table pollData )
```

Fired before a poll is starting. Allow other resources to modify the poll. Use onPollModified to send the poll back.

### onPollModified

``` lua
void onPollModified ( table pollData )
```

You can use it to send the modified poll.

### onPollStart

``` lua
void onPollStart (  )
```

Fired before a poll starts. Cancelling it aborts the poll.

### onPollStop

``` lua
void onPollStop (  )
```

Fired before a poll is halted. Cancelling it prevents the poll from being halted.

### onPollEnd

``` lua
void onPollEnd ( chosenOption )
```

Fired after a poll finished. Cancelling it has no effect.
**chosenOption**: Returns a number of the chosen option.

### onPollDraw

``` lua
void onPollDraw (  )
```

Fired when a poll ends in a draw. Cancelling it aborts renominations.

### onClientSendVote

``` lua
void onClientSendVote ( int vote )
```

Fired when a vote is sent to the server. *client* is the client who sent the vote. Cancelling it makes the manager ignore the client's choice.

Default settings
----------------

``` xml
<settings>
    <setting name="*color" value="#DF6464" />
    <setting name="*log_votes" value="[true]" />

    <setting name="*default.timeout" value="[30]"/>
    <setting name="*default.allowchange" value="[false]"/>
    <setting name="*default.percentage" value="[75]"/>
    <setting name="*default.maxnominations" value="[3]"/>

    <setting name="*votemap.enabled" value="[true]"/>
    <setting name="*votemap.timeout" value="[30]"/>
    <setting name="*votemap.locktime" value="[60]"/>
    <setting name="*votemap.percentage" value="[70]"/>
    <setting name="*votemap.allowchange" value="[true]"/>
    
    <setting name="*votekick.enabled" value="[true]"/>
    <setting name="*votekick.timeout" value="[30]"/>
    <setting name="*votekick.locktime" value="[120]"/>
    <setting name="*votekick.percentage" value="[75]"/>
    <setting name="*votekick.allowchange" value="[true]"/>
    
    <setting name="*voteban.enabled" value="[false]"/>
    <setting name="*voteban.timeout" value="[30]"/>
    <setting name="*voteban.locktime" value="[120]"/>
    <setting name="*voteban.percentage" value="[85]"/>
    <setting name="*voteban.allowchange" value="[true]"/>
    
    <setting name="*votekill.enabled" value="[true]"/>
    <setting name="*votekill.timeout" value="[30]"/>
    <setting name="*votekill.locktime" value="[120]"/>
    <setting name="*votekill.percentage" value="[75]"/>
    <setting name="*votekill.allowchange" value="[true]"/>

</settings>
```

[ru:<Resource:Votemanager>](/ru:Resource:Votemanager.md "wikilink")
