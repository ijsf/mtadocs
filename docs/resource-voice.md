The introduction of voice support in 1.1 comes with very basic, yet flexible scripting interface for it.

The purpose of the **Voice** resource is to provide a typical interface which wraps on top of MTA's own basic scripting, to provide typical features a user would expect of voice chat - including team assignment, channel assignment, and muting.

The **Voice** resource currently does not provide a GUI interface for muting other players clientside, though this is planned.

Concepts
========

The Voice resource provides **channel** functionality. A channel is a way of controlling who you can speak to and hear from. There are three main types of channels:

-   **Scripted channel:** This channel is set using the [setPlayerChannel](/docs/resource-voice#getplayerchannel.md "wikilink") function, and is in the format of a number. Players in channel *1* cannot hear players who are in channel *2*.

<!-- -->

-   **Team channel:** Scripts do not have access to this type of channel, but it is quite similar to a scripted channel. This type of channel is automatically assigned based upon the [Team autoassignment](/docs/resource-voice#team_autoassignment.md "wikilink") setting. When players are in a team, [getPlayerChannel](/docs/resource-voice#getplayerchannel.md "wikilink") will return the actual [team](/docs/team.md "wikilink") element. Players of one team channel cannot hear players in another team channel. Equally, players in a team channel cannot hear players in a *Scripted Channel*.

<!-- -->

-   **The “root” channel:** Players are placed into this channel by default. This channel is associated to the [root](/docs/getrootelement.md "wikilink") element concept, and [getPlayerChannel](/docs/resource-voice#getplayerchannel.md "wikilink") will actually return the root element. When a player is in the root channel, he is broadcasting to **everyone** in the server, and they will be able to hear him. However, he will not be able to hear from people who are either in a *Team channel* or a *Scripted channel*.

Settings
========

All settings can be modified using MTA's set() functions, modifying the meta.xml of the resource, or modifying the settings.xml.

### Chat Icons

-   **Setting name:** *show\_chat\_icon*
-   **Description:** A boolean value which allows you to disable or enable the voice chat broadcast icon that appears above a player when he speaks.
-   **XML Example:**
    ``` xml
    "/>
    ```

### Team autoassignment

-   **Setting name:** *autoassign\_to\_teams*
-   **Description:** A boolean value which allows you to disable or enable the voice resource automatically managing players into voice channels according to the team they're in.
-   **XML Example:**
    ``` xml
    "/>
    ```

Clientside Scripting functions
==============================

All these scripting functions are **clientside** and therefore only affect the **local player**. All functions must be called using the [exports](/docs/call.md "wikilink") system.

### isPlayerVoiceMuted

This function allows you to determine if a remote player is muted to the local player. In other words, can I hear this other player?

``` lua
bool exports.voice:isPlayerVoiceMuted ( player playerToCheck )
```

-   **playerToCheck:** The player for which you wish to check if they are muted

Returns a bool - *'true* if muted, **false** if not

### setPlayerVoiceMuted

This function allows you to set whether a remote player is muted to the local player. In simple terms, I can set whether I can hear this other player.

``` lua
bool exports.voice:setPlayerVoiceMuted ( player playerToMute, bool muted )
```

-   **playerToMute:** The player for which you wish to mute or unmute
-   **muted :** A bool of whether they should be muted or unmuted. **true** for muted, **false** for unmuted.

Returns a **true** if the operation was successful, **false** otherwise

Serverside Scripting functions
==============================

All these scripting functions are **serverside** and can affect all players in the server. All functions must be called using the [exports](/docs/call.md "wikilink") system.

### isPlayerVoiceMuted

This function allows you to determine if a player is muted to everyone in the server.

``` lua
bool exports.voice:isPlayerVoiceMuted ( player playerToCheck )
```

-   **playerToCheck:** The player for which you wish to check if they are muted

Returns a bool - *'true* if muted, **false** if not

### setPlayerVoiceMuted

This function allows you to set whether a player is muted to everyone in the server.

``` lua
bool exports.voice:setPlayerVoiceMuted ( player playerToMute, bool muted )
```

-   **playerToMute:** The player for which you wish to mute or unmute
-   **muted :** A bool of whether they should be muted or unmuted. **true** for muted, **false** for unmuted.

Returns a **true** if the operation was successful, **false** otherwise

### getPlayerMutedByList

This function allows you to retrive a list of the players who have muted a specified player

``` lua
table exports.voice:getPlayerVoiceMutedByList( player playerToCheck )
```

-   **playerToCheck:** The player who you wish to retrieve the list of who has muted this player

Returns a table of players who have muted the specified player.

### getPlayerChannel

This function allows you to get what voice chat channel the specified player is in.

``` lua
int/element exports.voice:getPlayerChannel ( player playerToCheck )
```

-   **playerToCheck:** The player who you wish to retrieve the channel of

Returns an integer of the channel ID they are in, or a [team](/docs/team.md "wikilink") element if they have been assigned to a team channel, or the [root](/docs/getrootelement.md "wikilink") element if they are not in a specific channel.

### setPlayerChannel

This function allows you to set what voice chat channel the specified player is in.

``` lua
bool exports.voice:setPlayerChannel ( player playerToCheck, [ int channelID ] )
```

-   **playerToCheck:** The player who you wish to set the channel of
-   **channelID :** *Optional:* The channel ID you wish to assign to this player. Not passing this argument will allow the Voice resource to automatically manage this player (e.g. Team assignment).

Returns **true** if the operation was successful, **false** otherwise.

### getPlayersInChannel

This function allows you to retrive a list of the players who are in a certain channel.

``` lua
table exports.voice:getPlayersInChannel ( int channelID )
```

-   **channelID :** The channelID which you want to get the list of players from.

Returns a table of players are in the specified channel.

### getNextEmptyChannel

This function allows you to get the next channel ID which is completely empty, allowing for easy creation of new channels

``` lua
int getNextEmptyChannel ( )
```

Returns an integer of the first channel ID which is completely empty.

[ru:<Resource:Voice>](/docs/ru-resource-voice.md "wikilink")
