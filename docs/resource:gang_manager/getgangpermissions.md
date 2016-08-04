Gets current permissions of the gang.

Syntax
------

``` lua
int int int int int int getGangPermissions ( string Gang )
```

### Required Arguments

-   **Gang:** ID of the gang you wish to get permissions of

### Returns

-   **MinSettings:** Minimal member level required to edit settings
-   **MinRules:** Minimal member level required to edit rules
-   **MinDeposit:** Minimal member level required to deposit money
-   **MinWithdraw:** Minimal member level required to withdraw money
-   **MinLevel:** Minimal member level required to change level of members with lower level
-   **MinInvKick:** Minimal member level required to invite and kick members with lower level
