This event is triggered when an accounts data changes through [setAccountData](/setAccountData.md "wikilink")

Parameters
----------

``` lua
account theAccount, string theKey, var theValue
```

-   **theAccount**: The account getting its data changed
-   **theKey**: The key that is being changed
-   **theValue**: The value it is changing to

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the root element.

Example
-------

This examples prevents the key of “level” being added or changed on every account

``` lua
function preventLevelChange(account, key, value)
    if (key == "level") then
        cancelEvent()
    end
end
addEventHandler("onAccountDataChange", root, preventLevelChange)
```

This examples logs every single account data change to server log

``` lua
function preventLevelChange(account, key, value)
    if (wasEventCancelled()) then return end -- If the data change was aborted don't log it.
    outputServerLog(getAccountName(account).." key: "..key.." changed to: "..tostring(value))
end
addEventHandler("onAccountDataChange", root, preventLevelChange)
```
