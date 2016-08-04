Matrices are one of the most powerful features of MTA [OOP](/docs/oop.md "wikilink"). We did have a presence of Matrices before with [getElementMatrix](/docs/getelementmatrix.md "wikilink"), but we were given an ugly disgusting table to play with. Now, with the new Matrix class, we can make and magically manipulate Matrices.

Methods
-------

### create

This is default constructor for the Matrix class and returns a Matrix object. You can instantiate a Matrix object in several ways, as described below.

``` lua
 )
```

-   **position**: The position vector of the matrix
-   **rotation**: The rotation vector of the matrix

``` lua
matrix Matrix ( Matrix matrixToClone )
```

-   **matrixToClone**: A matrix you want to make a clone of

``` lua
matrix Matrix()
```

-   You can call this method without parameters to initialize a zero matrix

### transformPosition

This method transforms a given position vector using the Matrix.

``` lua
Vector3 Matrix:transformPosition ( Vector3 position )
```

-   **position**: The position vector you want to transform

#### Example

This example teleports a random player to a location 5 meters in front of him

``` lua
local player = getRandomPlayer()
local desiredRelativePosition = Vector3(0, 5, 0) -- 5 meters front of player is a y = 5 vector
local matrix = player.matrix
local newPosition = matrix.transformPosition(desiredRelativePosition)
player.position = newPosition
```

### getPosition

This method returns the position vector of a given matrix.

``` lua
Vector3 Matrix:getPosition()
```

#### Example

This example prints the position of a random player.

``` lua
local player = getRandomPlayer()
local matrix = player.matrix
local position = matrix:getPosition()
outputChatBox("x: " .. position:getX() .. ", y: " .. position:getY() .. ", z:" .. position:getZ())
```

### getRotation

### getForward

### getRight

### getUp

Using Matrices
--------------

Say you wanted to create a bin - object 1337 - two units in front of a player. You don't want to manually do trigonometry and you don't want to play with the complicated tables. You just want to get the position two units in front of the player whilst taking into account the rotation of the player. You only need to use **[Matrix.getForward](/docs/matrix#getforward.md "wikilink")**, **[Matrix.getPosition](/docs/matrix#getposition.md "wikilink")** and **[getElementMatrix](/docs/getelementmatrix.md "wikilink")**. It's just:

``` lua
Object ( 1337, player.matrix.position + player.matrix.forward * 2 )
```

Why not stick to the good ol' tables?
-------------------------------------

Say you'd like to get find the position underneath a vehicle. This is the position at any rotation. So if it was upside down, the Z value would be higher than the vehicle Z value. If the vehicle was the right way round, the Z value for underneath car would be less than the Z value for the car.

``` lua
--
-- Instead of:
--
local matrix = getElementMatrix(vehicle)
local offX = 0 * matrix[1][1] + 0 * matrix[2][1] - 1 * matrix[3][1] + matrix[4][1]
local offY = 0 * matrix[1][2] + 0 * matrix[2][2] - 1 * matrix[3][2] + matrix[4][2]
local offZ = 0 * matrix[1][3] + 0 * matrix[2][3] - 1 * matrix[3][3] + matrix[4][3]

local pX, pY, pZ = getElementPosition(vehicle)
local positionBelow = {offX-pX, offY-pY, offZ-pZ}

--
-- You only have to do:
--
local positionBelow = vehicle.position - vehicle.matrix.up
```

[ru:Matrix](/docs/ru-matrix.md "wikilink") [Category:OOP](/docs/category-oop.md "wikilink")
