MTA uses a database system based on files. This system is sqlite, an embedded relational database management system.

Files
-----

There are two main database files for storing data:

-   **internal.db:** this contains user account data (usernames, passwords and account data stored by using the [setAccountData](/docs/setaccountdata.md "wikilink") and [getAccountData](/docs/getaccountdata.md "wikilink") functions.
-   **registry.db:** this is the main database file, all the executeSQL\* scrtipting functions work with this file.

Functions
---------
