# Instruction reference #

## 0 ##

_Takes no parameters._


## 1 ##

_Takes no parameters._

A _return_ instruction.


## 10 ##

_Takes no parameters._

A _return_ instruction.


## 11 ##

| Type | Description |
|:-----|:------------|
| **string** | Subroutine name. |
| ... | Optional parameters. |

Calls a subroutine and passes it a number of parameters.

The parameters have a special representation in the data files: a type indicator, and then the data value.
The data value can be either an integer or a float.
The type indicator can indicate three things,

  1. That the data is of float type. (0x6666)
  1. That the data is of integer type, but is used as a float type. (0x6669)
  1. That the data is of integer type. (0x6969)

In the current syntax this is represented by prefixing the data with either **(int)** or **(float)**.

The parameters seem to end up on the stack of the called subroutine.


## 12 ##

| Type | Description |
|:-----|:------------|
| **integer** | Relative jump offset. |
| **time** | New time value. |

Jumps to another instruction.
The offset is calculated by subtracting the location of the current instruction from the location of the target instruction.
Labels can be used to calculate this automatically.

The current time is also changed.


## 13 ##

| Type | Description |
|:-----|:------------|
| **integer** | Relative jump offset. |
| **time** | New time value. |

Jumps when the top of the arithmetic stack is equal to 0.

Refer to [instruction 12](#12.md).


## 14 ##

| Type | Description |
|:-----|:------------|
| **integer** | Relative jump offset. |
| **time** | New time value. |

Jumps when the top of the arithmetic stack is not equal to 0.

Refer to [instruction 12](#12.md).


## 15 ##

| Type | Description |
|:-----|:------------|
| **string** |  |
| ... |  |

Refer to [instruction 11](#11.md).


## 16 ##

| Type | Description |
|:-----|:------------|
| **string** | Subroutine name. |
| **integer** | Index. |

Runs a subroutine in the background and assigns it the given slot.


## 17 ##

| Type | Description |
|:-----|:------------|
| **integer** | Index. |

Terminates a subroutine launched with [instruction 16](#16.md).


## 21 ##

_Takes no parameters._


## 40 ##

| Type | Description |
|:-----|:------------|
| **integer** | Stack size. |

Sets up the stack which is used for local variables and passed parameters.
The stack size should be a multiple of four.


## 42 ##

| Type | Description |
|:-----|:------------|
| **integer** | Value. |

Pushes a value onto the arithmetic stack.


## 43 ##

| Type | Description |
|:-----|:------------|
| **integer** | Stack offset. |

Stores the value at the top of the arithmetic stack at the given stack offset.


## 44 ##

| Type | Description |
|:-----|:------------|
| **float** |  |

Pushes a value onto the arithmetic stack.
Might be intended for floats.


## 45 ##

| Type | Description |
|:-----|:------------|
| **float** |  |

Stores the value at the top of the arithmetic stack at the given stack offset.
Might be intended for floats.


## 50 ##

_Takes no parameters._

Addition operator.


## 51 ##

_Takes no parameters._

Addition operator.
Might be intended for floats.


## 52 ##

_Takes no parameters._

Subtraction operator.


## 53 ##

_Takes no parameters._

Subtraction operator.
Might be intended for floats.


## 54 ##

_Takes no parameters._

Multiplication operator.


## 55 ##

_Takes no parameters._

Multiplication operator.
Might be intended for floats.


## 56 ##

_Takes no parameters._

Division operator.


## 57 ##

_Takes no parameters._

Division operator.
Might be intended for floats.


## 58 ##

_Takes no parameters._

Modulo operator.


## 59 ##

_Takes no parameters._

Equality operator.


## 61 ##

_Takes no parameters._

Inequality operator.


## 63 ##

_Takes no parameters._

Less-than operator.


## 64 ##

_Takes no parameters._

Less-than operator.
Might be intended for floats.


## 65 ##

_Takes no parameters._

Less-than-or-equal-to operator.


## 67 ##

_Takes no parameters._

Greater-than operator.


## 68 ##

_Takes no parameters._

Greater-than operator.
Might be intended for floats.


## 69 ##

_Takes no parameters._

Greater-than-or-equal-to operator.


## 70 ##

_Takes no parameters._

Greater-than-or-equal-to operator.
Might be intended for floats.


## 71 ##

_Takes no parameters._

Boolean not operator.


## 73 ##

_Takes no parameters._

Boolean or operator.


## 74 ##

_Takes no parameters._

Boolean and operator.


## 78 ##

| Type | Description |
|:-----|:------------|
| **integer** | Stack offset. |

Decrements the value passed and pushes its old value onto the arithmetic stack.


## 79 ##

_Takes no parameters._


## 81 ##

| Type | Description |
|:-----|:------------|
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |


## 82 ##

| Type | Description |
|:-----|:------------|
| **float** |  |


## 83 ##

| Type | Description |
|:-----|:------------|
| **time** | Time to wait. |

Wait the the specified time before continuing.


## 85 ##

_Takes no parameters._


## 256 ##

| Type | Description |
|:-----|:------------|
| **string** | Subroutine name. |
| **coordinate** | Starting x position. |
| **coordinate** | Starting y position. |
| **integer** | Hit points. |
| **integer** | Score reward. |
| **integer** | Item dropped when destroyed. |

Create an "object", i.e. an enemy or something that can move around.
The subroutine is called to set up and control the object.

Items dropped (0 for nothing):

  1. Small powerup.
  1. Point item.
  1. Large green star.
  1. Large powerup.
  1. Full-score point item.
  1. Full-power powerup.
  1. 1-up.
  1. An autocollecting yellow orb.
  1. Small green star.


## 257 ##

| Type | Description |
|:-----|:------------|
| **string** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |

No differences from [instruction 256](#256.md) have been observed.


## 258 ##

| Type | Description |
|:-----|:------------|
| **integer** | ANM include index. |

Selects which ANM file to use for further animation operations.
1 refers to the first file listed, and 2 to the second.
0 appears to have some special meaning.


## 259 ##

| Type | Description |
|:-----|:------------|
| **integer** | ? |
| **integer** | Animation index. |

Selects an animation for an object.
The animation indices are listed in the ANM files, and contain their own animation script.

The first parameter might allow for attaching several sprites to an object.


## 260 ##

| Type | Description |
|:-----|:------------|
| **string** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |

No differences from [instruction 256](#256.md) have been observed.


## 261 ##

| Type | Description |
|:-----|:------------|
| **string** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |

No differences from [instruction 256](#256.md) have been observed.


## 262 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |

Similar to [instruction 257](#257.md).


## 263 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |


## 264 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |


## 265 ##

| Type | Description |
|:-----|:------------|
| **string** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |

No differences from [instruction 256](#256.md) have been observed.


## 266 ##

| Type | Description |
|:-----|:------------|
| **string** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |

No differences from [instruction 256](#256.md) have been observed.


## 267 ##

| Type | Description |
|:-----|:------------|
| **string** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |

No differences from [instruction 256](#256.md) have been observed.


## 268 ##

| Type | Description |
|:-----|:------------|
| **string** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |

No differences from [instruction 256](#256.md) have been observed.


## 269 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |

Related to animation.


## 270 ##

| Type | Description |
|:-----|:------------|
| **string** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |

Similar to [instruction 256](#256.md).
Adds a third float parameter.


## 272 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |


## 273 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |


## 280 ##

| Type | Description |
|:-----|:------------|
| **coordinate** | Target x position. |
| **coordinate** | Target y position. |

Instantly moves an object to the specified position.


## 281 ##

| Type | Description |
|:-----|:------------|
| **time** | Move duration. |
| **integer** | Movement mode. |
| **coordinate** | Target x position. |
| **coordinate** | Target y position. |

Moves the object to the specified position in the specified time.

The movement mode controls how the object moves to the target position, but the time it takes is the same.
0 is normal movement, 1 accelerates and stops suddenly, 4 moves in an interpolated manner.


## 282 ##

| Type | Description |
|:-----|:------------|
| **float** |  |
| **float** |  |


## 283 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |
| **integer** |  |


## 284 ##

| Type | Description |
|:-----|:------------|
| **angle** | Direction. |
| **float** | Speed. |

Sets movement direction and speed for an object.
The speed might be pixels per frame.


## 285 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |
| **float** |  |

Similar to [instruction 285](#285.md).
Maybe it is used to change from one movement to another.


## 286 ##

| Type | Description |
|:-----|:------------|
| **float** |  |
| **float** |  |


## 287 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |
| **float** |  |


## 288 ##

| Type | Description |
|:-----|:------------|
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |


## 290 ##

| Type | Description |
|:-----|:------------|
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |


## 291 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **integer** |  |


## 292 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |


## 294 ##

_Takes no parameters._


## 296 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |


## 298 ##

| Type | Description |
|:-----|:------------|
| **float** |  |
| **float** |  |


## 299 ##

| Type | Description |
|:-----|:------------|
| **float** |  |
| **float** |  |


## 320 ##

| Type | Description |
|:-----|:------------|
| **float** | Hitbox width. |
| **float** | Hidbox height. |

Sets up a hitbox for an object.
It is not disabled by setting both parameters to 0.0f.


## 321 ##

| Type | Description |
|:-----|:------------|
| **float** | Killbox width. |
| **float** | Killbox height. |

Sets up a killbox (the area which kills the player) for an object.
It can be disabled by setting both parameters to 0.0f.


## 322 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |

Appears to set flags for objects, such as if it has a hitbox or not.


## 323 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |


## 324 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **float** |  |
| **float** |  |
| **float** |  |


## 325 ##

_Takes no parameters._

Related to item drops.


## 326 ##

_Takes no parameters._

Clears the list of items to be dropped.


## 327 ##

| Type | Description |
|:-----|:------------|
| **integer** | Item. |
| **integer** | Count. |

Sets up which [items](#256.md) are dropped when this object is defeated (in addition to the one specified by the creation instruction).
Can be called several times for more items.


## 328 ##

| Type | Description |
|:-----|:------------|
| **float** | Width. |
| **float** | Height. |

Sets up an area in which items are dropped.


## 329 ##

_Takes no parameters._

Drops all loaded items.


## 330 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |


## 331 ##

| Type | Description |
|:-----|:------------|
| **integer** | Hit points. |

Changes the hit points of an object.


## 332 ##

| Type | Description |
|:-----|:------------|
| **integer** | Flag. |

Enables or disables "boss mode" (hit point bar, and name display).
Enabled with 0 and disabled with -1.


## 333 ##

_Takes no parameters._


## 334 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **time** | Time. |
| **string** | Subroutine name. |

Sets up a condition for a boss.
For example the specified subroutine can be called after a period of time has passed.
It can also be used for hit points.


## 335 ##

| Type | Description |
|:-----|:------------|
| **time** | Invulnerability duration. |

Makes the object invulnerable for the specified period of time.


## 336 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |


## 337 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **integer** |  |


## 338 ##

| Type | Description |
|:-----|:------------|
| **integer** | Dialogue index. |

Initiates dialogue.
The first dialogue has index 0.


## 339 ##

_Takes no parameters._


## 340 ##

_Takes no parameters._


## 341 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **string** |  |


## 342 ##

| Type | Description |
|:-----|:------------|
| **integer** | Spell card number. |
| **time** | Spell card bonus timer. |
| **integer** |  |
| **cstring** | Spell card name. |

Set up a spell card.
One is added to the spell card number to get the number displayed in-game.


## 343 ##

_Takes no parameters._


## 344 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |


## 345 ##

_Takes no parameters._


## 346 ##

| Type | Description |
|:-----|:------------|
| **float** |  |


## 347 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **float** |  |
| **integer** |  |


## 355 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |


## 356 ##

| Type | Description |
|:-----|:------------|
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |


## 357 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **cstring** |  |

No differences from [instruction 342](#342.md) have been observed.


## 359 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **cstring** |  |

No differences from [instruction 342](#342.md) have been observed.


## 360 ##

| Type | Description |
|:-----|:------------|
| **integer** | Number of spell card stars. |

Sets the number of spell cards remaining, as indicated by a series of stars.
Requires [boss mode](#332.md) for the stars to show up.


## 361 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |


## 362 ##

_Takes no parameters._


## 363 ##

_Takes no parameters._


## 364 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |


## 365 ##

_Takes no parameters._


## 366 ##

| Type | Description |
|:-----|:------------|
| **integer** | Flag. |
| **integer** | Animation index. |

Enables or disables bomb-invulnerability for an object.
Set the flag to 1 to enable or 0 to disable it.
The object's animation is changed as specified for the duration of the bomb.


## 367 ##

| Type | Description |
|:-----|:------------|
| **float** |  |


## 368 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |


## 400 ##

| Type | Description |
|:-----|:------------|
| **integer** | Bullet type. |

Might initialize a new bullet type.
Eight different bullet types have been observed.


## 401 ##

| Type | Description |
|:-----|:------------|
| **integer** | Bullet type. |

Fires a bullet of the specified type.


## 402 ##

| Type | Description |
|:-----|:------------|
| **integer** | Bullet type. |
| **integer** |  |
| **integer** |  |

Sets the bullet type appearance.


## 403 ##

| Type | Description |
|:-----|:------------|
| **integer** | Bullet type. |
| **float** | x offset. |
| **float** | y offset. |

Makes bullets spawn in a position offset from the object which fires them.


## 404 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **float** |  |
| **float** |  |


## 405 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **float** |  |
| **float** |  |


## 406 ##

| Type | Description |
|:-----|:------------|
| **integer** | Bullet type. |
| **integer** | Bullet count. |
| **integer** | Extra bullets. |

The bullet count parameter can be used to fire walls or circles of bullets
The extra parameter fires additional bullets, each at half the speed of the previous.


## 407 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |


## 409 ##

| Type | Description |
|:-----|:------------|
| **integer** | Bullet type. |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **float** |  |
| **float** |  |

Might set up random bullet attributes.


## 410 ##

_Takes no parameters._


## 411 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |


## 412 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **float** |  |


## 413 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **float** |  |
| **integer** |  |


## 420 ##

| Type | Description |
|:-----|:------------|
| **float** |  |


## 421 ##

| Type | Description |
|:-----|:------------|
| **float** |  |


## 425 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |


## 428 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **float** |  |
| **integer** |  |
| **float** |  |


## 431 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **float** |  |
| **float** |  |
| **float** |  |


## 433 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **float** |  |
| **float** |  |
| **integer** |  |
| **float** |  |
| **float** |  |
| **float** |  |


## 435 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |
| **float** |  |


## 436 ##

| Type | Description |
|:-----|:------------|
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |
| **integer** |  |