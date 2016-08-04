This function retrieves the squad ID. The squad ID is simply a string representing the full squad name. The first letter of a squad name is the ID. It can be retrieved with the squad element.
Alpha Bravo Charlie Delta Echo Foxtrot Golf Hotel

Syntax
------

``` lua
 string getSquadID ( team squadTeam, squad squadElement ) 
```

Required Arguments
==================

-   **squadTeam**: The team element the squad is attached to. if this is nil or false then it checks the second argument (squadElement).
-   **squadElement**: The squad you want the ID/shortn from.

[<Resource:battlefield>](/docs/resource-battlefield.md "wikilink")
