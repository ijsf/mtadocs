This function allows you to set or remove read-only status for an edit box. If read-only is set to *true*, the box is not editable.

Syntax
------

``` lua
bool guiEditSetReadOnly ( element editField, bool status )
```

### Required Arguments

-   **editField:** The element of the [edit field](/Element/GUI/Edit_field.md "wikilink") to be modified.
-   **status:** A boolean value indicating whether read-only is to be enabled or disabled.

### Returns

Returns *true* if edit field's read-only status was changed successfully, *false* otherwise.

Example
-------

This example creates a little advert field on the bottom right corner of the screen and sets it to read only.

``` lua
myWebsite = "development.mtasa.com" -- define the text to be displayed in advert field
function createAdvert( )
    local advert = guiCreateEdit( 0.845, 0.94, 0.15, 0.05, myWebsite, true ) -- create edit field for the advert
    if advert then -- if it was successfully created
        guiEditSetReadOnly( advert, true ) -- make it read only
    end
end
addEventHandler ( "onClientResourceStart", getResourceRootElement( getThisResource() ), createAdvert )
```

See Also
--------
