Syntax
------

``` lua
table getLocalization ( )
```

### Returns

Returns a [table](/docs/table.md "wikilink") with the following entries:

-   **code :** The language code *(eg. “en\_US” for “English (United States)” or “ar” for “Arabic”)*.
-   **name :** The name of the language *(eg. “English (United States)” or “Arabic”)*.

Example
-------

This example outputs simple *Welcome* message at the resource start (also when player joins the game if the resource is already running).

``` lua
local msg = {cs = "Vítejte", fr = "Accueil", de = "Willkommen", pl = "Powitanie"}

addEventHandler("onClientResourceStart", resourceRoot, 
    function ()
        local languageCode = getLocalization()["code"]
        if msg[languageCode] then --Check if the message is avaible in client's language
            outputChatBox(msg[languageCode] .. "!") --Output it
        else
            outputChatBox("Welcome!") --Output English for any other language
        end
    end)
```

See Also
--------

[ru:GetLocalization](/docs/ru:GetLocalization.md "wikilink")
