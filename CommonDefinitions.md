## Data types ##

Actual data types present in the data files.

**integer** -
An integer value expressed either as decimal or hexadecimal: `10`, `0xa`.
Has 31 bits of precision and a sign bit unless otherwise is specified.

**float** -
Specified in scripts as a real number followed by the character f: `1.01f`.
Represented using the IEEE 754 binary32 format.

**string** -
A sequence of data enclosed by two double quote characters: `"Test"`.
Double quote characters can not be escaped at the moment.

**cstring** -
A sequence of data that is encrypted when stored in data form.
The same as a string, but prefixed by the character C: `C"Test"`

## Refined data types ##

Normal data types interpreted in specific ways.

**coordinate** -
(**float**)
An on-screen coordinate.
The two coordinates (0.0f, 0.0f) are the center and top of the playing field.
X increases to the right, and Y to the bottom.

**angle** -
(**float**)
An amount of rotation measured in radians with 0.0f to the right and pi/2 down.

**time** -
(**integer**)
A count of frames, where one frame is 1/60th of a second.

## Common definitions ##

**operator** -
An operator takes two parameters, performs an operation on them, and returns the result.
In scripts the parameters are the "arithmetic stack", from which the values are popped, and the return value is also pushed onto the stack.

**subroutine** -
A list of instructions with a name attached.
Executing a subroutine executes instructions in order, with exceptions for control flow instructions.

**instruction** -
Commands which instruct the game engine to perform different actions.
Can often be customized further by provided parameters.

**parameter** -
Parameters to instructions which change their behavior.

**identifier** -
A letter followed by letters and numbers: `Test`

**animation** -
A sequence of instructions which describe how to display and animate sprites.

**sprite map** -
A large field of pixels which contains a number of sprites.

**sprite** -
A rectangular (often a power of two square) set of pixels.

**rank** -
Also known as "level" or "difficulty".
Easy, Normal, Hard, or Lunatic.