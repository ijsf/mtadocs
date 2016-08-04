Syntax
------

``` lua
bool isBrowserSupported ( )
```

### Returns

Returns *true* if the client is supported and can use the web browser (i.e. it is running Windows 7 or greater as its operating system). If not, it returns *false*.

Examples
--------

This example outputs a warning to the chatbox when a player that can't view web browsers joins. Keep in mind that MTA automatically remembers them that they should update their operating system in order to support CEF.

``` lua
-- Cannot we use the browser? Then that means we are on XP or Vista
if not isBrowserSupported() then
    outputChatBox("Hey, are you using Windows XP or Vista these days? If you aren't emulating it, that's truly amazing!")
end
```

See also
--------
