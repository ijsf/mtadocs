This function allows retrieval of where a player's target is blocked. It will only be blocked if there is an obstacle within a player's target range.

Syntax
------

``` lua
float float float getPlayerTargetCollision ( player targetingPlayer )
```

### Required Arguments

-   **targetingPlayer:** This is the player whose target collision you wish to retrieve

### Returns

Returns three floats, *x*,*y*,*z*, representing the position where the player's target collides, or false if it was unsuccessful.

Example
-------

This page does not have an example.

``` lua
--add an example here
```

See Also
--------
