This function returns whether the file downloading dialog box is active or not. This appears when a resource is started and the client doesn't have all the files that resource requires the client to have.

It's important to note that resources aren't started on the client until they're completely downloaded, so a resource cannot use this function to detect if it's own files are downloaded. A client-side resource triggers the [onClientResourceStart](/docs/onclientresourcestart.md "wikilink") event when the files it requires are downloaded.

Syntax
------

``` lua
bool isTransferBoxActive ()
```

### Returns

Returns *true* if the file transfer box is visible, *false* if not.

Example
-------

This makes the camera fade in, once all resource downloads are finished.

``` lua
resourceRoot = getResourceRootElement(getThisResource())
function checkTransfer()
    if isTransferBoxActive() == true then
        setTimer(checkTransfer,2000,1) -- Check again after 2 seconds
    else 
        fadeCamera(true)  -- TransferBox isnt active, fade in camera
    end
end
addEventHandler("onClientResourceStart",resourceRoot,checkTransfer)
```

See Also
--------
