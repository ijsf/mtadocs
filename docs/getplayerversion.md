This function gets the client version of the specified [player](/docs/player.md "wikilink") as a sortable string. The string is always 15 characters long and is formatted as follows:

-   1 character representing the major version
-   1 dot character
-   1 character representing the minor version
-   1 dot character
-   1 character representing the maintenance version
-   1 dash character
-   1 character representing the build type
-   1 dot character
-   5 characters representing the build number
-   1 dot character
-   1 character representing the build revision

An example of a version string would be: 1.0.4-9.01746.0

Where the first three numbers represent the major/minor/maintenance version, i.e. 1.0.4
The fourth number is 9, which means it's a release build, (Development and beta builds have lower numbers here)
And the fifth and sixth numbers represent the build number.

Syntax
------

``` lua
string getPlayerVersion ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") whose client version you wish to get.

### Returns

Returns a string containing the client version, or false if the [player](/docs/player.md "wikilink") is invalid.

Example
-------

<section name="Server" class="server" show="true">
This example adds a command that allows players to see their own client version.

``` lua
function showMeMyVersion( playerSource )
    local version = getPlayerVersion ( playerSource )
    outputChatBox ( "Your client version is: " .. version, playerSource )
end

addCommandHandler ( "myversion", showMeMyVersion )
```

</section>
See Also
--------
