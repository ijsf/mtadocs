Sets permission levels of the gang.

Syntax
------

``` lua
bool setGangPermissions ( string Gang, integer MinSettings, integer MinRules, integer MinDeposit, integer MinWithdraw, integer MinLevel, integer MinInvKick )
```

### Required Arguments

-   **Gang:** ID of the gang you wish to set permissions of
-   **MinSettings:** Minimal member level required to edit settings
-   **MinRules:** Minimal member level required to edit rules
-   **MinDeposit:** Minimal member level required to deposit money
-   **MinWithdraw:** Minimal member level required to withdraw money
-   **MinLevel:** Minimal member level required to change level of members with lower level
-   **MinInvKick:** Minimal member level required to invite and kick members with lower level

### Returns

-   **Success:** Boolean that is true if gang permissions were successfully set
