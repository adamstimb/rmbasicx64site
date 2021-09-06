---
layout: default
title: Reference
nav_order: 5
---

# Reference

---

This reference defines all the commands currently implemented in RM BASICx64 with details of any deviations from the original RM Basic implementation.  To learn RM Basic itself I recommend reading the original RM Basic manual, available for free and legal download from the [Centre for Computing History](http://www.computinghistory.org.uk/det/47278/RM-Nimbus-PC-RM-Basic-PN-14351/).

# Keywords

The format, punctuation and options are shown using the following symbols:

_..._
indicates the more items can be used

_exp, exp1_
numeric or string expression

_e, e1, ..._
numeric expressions

_e$, e1$, ..._
string expressions

_v, v1, ..._
variable names

_t_
a numeric expression that is evaluated as a boolean; a non-zero value is considered TRUE and 0 considered FALSE

_lineNumber, lineNumber ..._
program line numbers

## ABS

Calculate the absolute value of a number.

### Syntax

ABS(_e_)

### Example

```
PRINT ABS(-1.2345)

   1.2345

```

## AND

Bitwise AND on two expressions.

### Syntax

_e1_ AND _e2_

## AREA

Draw a filled polygon on the screen.

### Syntax

AREA _coordinateList_ [_optionList_]

### Remarks

The AREA command draws a shape by connecting each point from a coordinate list to the next, starting and finishing at the first point in the list.  Each coordinate is seperated by a semicolon, e.g. 0, 0; 50, 0; 50, 50; 0, 50

After the coordinate list you can specify options that override the current graphics settings:

| Option | Action | Syntax |
| ------ | ------ | ------ |
| BRUSH | selects the brush colour | BRUSH _e_ |
| STYLE | not yet implemented | n/a |
| OVER | selects the drawing style | OVER _t_ |

### Example

```
10 REM Draw a red triangle
20 SET MODE 40
30 AREA 0, 0; 100, 0; 50, 100 BRUSH 2
```

## ASK MOUSE

Get the current position and button state of the mouse.  

### Syntax

ASK MOUSE [_v1_, _v2_][, _v3_]

### Remarks

The mouse must first be initialised with the `SET MOUSE` command.  _v1_ and _v2_ are the variables in which the X and Y position of the mouse cursor will be stored.  Note that these are the positions on the Nimbus's screen; if the mouse is outside RM BASICx64 application window then only its last known on-screen position will be available.  _v3_ is the variable to store the button state (0 no button pressed, 1right-hand button pressed, 2 left-hand button pressed, 3 middle or both buttons pressed depending on your mouse and operating system).  Unlike original RM Basic, it is not possible to set the starting position or sensitivity of the mouse in RM BASICx64.

### Example

```
10 REM A simple drawing program
20 SET MODE 40
30 PRINT "Left-click to draw" ! "Right-click to quit"
40 SET MOUSE
50 REPEAT
60   ASK MOUSE Xpos%, Ypos%, Button%
70   REM Flicker the mouse cursor unless left button pressed
80   IF Button% = 1 THEN CIRCLE 5, Xpos%, Ypos% BRUSH 13 ELSE CIRCLE 5, Xpos%, Ypos% BRUSH 13 OVER FALSE
90 UNTIL Button% = 2
```

## ATN

Calculate the angle with the given tangent.  The unit of the measurement for the angle can be set with [SET DEG](#set-deg) or [SET RAD](#set-rad).

### Syntax

ATN(_e_)

### Example

```
SET DEG TRUE
PRINT ATN(1.557)

   90

```

## BYE

Quit the application.

## CIRCLE

Draw one or more circles on the screen.

### Syntax

CIRCLE _e_, _coordinateList_ [_optionList_]

### Remarks

_e_ is the radius of the circle.  The coordinate list can be a single set of coordinates or a list of several, seperated by a semicolon, e.g. 10, 200 or 10, 200; 20, 200; 30, 200

After the coordinate list you can specify options that override the current graphics settings:

| Option | Action | Syntax |
| ------ | ------ | ------ |
| BRUSH | selects the brush colour | BRUSH _e_ |
| STYLE | not yet implemented | n/a |
| OVER | selects the drawing style | OVER _t_ |

### Example

```
CIRCLE 20, 0, 200
CIRCLE 15, 50, 100 BRUSH 2
CIRCLE 30, 0, 150; 50, 150; 100, 150 BRUSH 1 OVER FALSE
```

## CLS

Clears the screen.

Clearing selected textboxes not yet implemented.

## COS

Calculate the cosine of an angle.  The unit of the measurement for the angle can be set with [SET DEG](#set-deg) or [SET RAD](#set-rad).

### Syntax

COS(_e_)

### Example

```
SET DEG TRUE
PRINT COS(90)

   -25.67272711536642

```

## DIR

Lists the BASIC program files in the workspace folder.

### Syntax

DIR

### Remarks

DIR does not yet support listing different folders or files without the .BAS extension.  The workspace folder is currently fixed to a subdirectory in your installation folder.  In a future release it should become possible to change this to something more suitable, e.g. a folder in My Documents.

## EDIT

Edit a line number in a program

### Syntax

EDIT _lineNumber_

## EXP

Calculate the exponential function, e^x

### Syntax

EXP(_e_)

### Example

```
PRINT EXP(1)

   2.718281828459045

```

## FOR ... NEXT

Repeat a series of instruction, altering a control variable on each repetition.

### Syntax

FOR _v_ [:]= _e1_ TO _e2_ [STEP _e3_]
:
Instructions
:
NEXT [_v_]

### Example

```
10 PRINT "Countdown"
20 FOR I% := 5 TO 0
30   PRINT I%
40 NEXT I%
50 PRINT "Blast off!"
RUN

  Countdown
  5
  4
  3
  2
  1
  0
  Blast off!
```

## GET

Read the code of a character from the keyboard if a key was pressed.

### Syntax

GET([_e_])

## GOTO

Interrupt the flow of the program and jump to any given line number.

### Syntax

GOTO _lineNumber_

### Example

```
10 REM This goes out to LGR
20 PRINT "Farts!"
30 GOTO 20
```

## HOME

Return the cursor to the top-left corner of the screen

### Syntax

HOME

## IF...THEN...ELSE

Conditionally execution instruction(s) on a single line.

### Syntax

IF _t_ THEN Instruction(s) [ELSE Instruction(S)]

### Example

```
IF Month = 9 THEN PRINT "September"
IF Month = 12 AND Day = 31 THEN SET PEN 2 : PRINT "Happy New Year!" ELSE SET PEN 1 : PRINT "Have a nice day!"
```

## INT(_e_)

Calculate the largest whole number that is less than or equal to a given value.

### Example 

```
PRINT INT(34.99999999)

   34

```

## LEN

Return the number of characters in a string.

### Syntax

LEN(_e$_)

```Example
PRINT LEN("Hello Mable")

   11

```

## LET

Assign the value of an expression to a variable.

### Syntax

[LET] v [:]= _e_
_or_
[LET] v$ [:]= _e$_

### Example

```
Cats% := 5
Dogs% = 1
Temperature := 18.57
Country$ := "Poland"
LET Total_Animals% := Cats% + Dogs%
```

## LINE

Draw a series of connected lines on the screen.

### Syntax

LINE _coordinateList_ [_optionList_]

### Remarks

The LINE command draws a shape by connecting each point from a coordinate list to the next.  Each coordinate is seperated by a semicolon, e.g. 0, 0; 50, 0; 50, 50; 0, 50

After the coordinate list you can specify options that override the current graphics settings:

| Option | Action | Syntax |
| ------ | ------ | ------ |
| BRUSH | selects the brush colour | BRUSH _e_ |
| STYLE | not yet implemented | n/a |
| OVER | selects the drawing style | OVER _t_ |

### Example

```
10 REM Draw a green wire triangle
20 SET MODE 40
30 LINE 0, 0; 100, 0; 50, 100; 0, 0 BRUSH 4
```

## LIST

List the stored program.  Listing over ranges yet to be implemented.

### Syntax

LIST

## LN

Calculate the natural logarithm of a number.

### Syntax

LN(_e_)

### Example

```
PRINT LN(1.32)

   0.27763173659827955

```

## LOAD

Load a program from a file into memory.

### Syntax

LOAD _e$_

### Remarks

Where _e$_ must be a valid filename.  If _e$_ does not end in ".BAS" then ".BAS" will be added automatically.

## LOG

Calculate the logarithm to the base 10 of a number.

### Syntax

LOG(_e_)

### Example

```
PRINT LOG(5.2)

   0.7160033436347991

```

## MOVE

Move the cursor relative to its current position.

### Syntax

MOVE _e1_, _e2_

### Remarks

_e1_ is the number of columns move, and _e2_ is the number of rows to move, relative to the current cursor position.

## NEW

Clear workspace.  Delete all variables and wipe the stored program.

### Syntax

NEW

## NOT

Bitwise NOT on an expression.

### Syntax

NOT _e_

## OR

Bitwise OR on two expressions.

### Syntax

_e1_ OR _e2_

## PLOT

Draw graphics characters on the screen.

### Syntax

PLOT _e$_, _coordinateList_ [_optionList_]

### Remarks

The PLOT command draws _e$_ at all the coordinates in the coordinateList.  Each coordinate is seperated by a semicolon, e.g. 0, 0; 50, 0; 50, 50; 0, 50

After the coordinate list you can specify options that override the current graphics settings:

| Option | Action | Syntax |
| ------ | ------ | ------ |
| BRUSH | selects the brush colour | BRUSH _e_ |
| OVER | selects the drawing style | OVER _t_ |
| DIRECTION | selects the drawing direction | DIRECTION _e_ |
| SIZE | selects the size of characters | SIZE _e1_[, _e2_] |
| FONT | selects the font of characters | FONT _e_ |

## PRINT

Prints strings and/or numbers on the screen.

### Syntax

PRINT [_print list_]

### Remarks

_print list_ is a list of expressions (numeric and/or string). Each expression must be separated by a semicolon, comma, space or exclamation mark.  The expressions are evaluated and then printed on screen.  Using semicolon or space between the expressions causes the results to be printed on the same line immediately following one another.  Using a comma causes the following result to be printed in the next print zone (this isn't properly implemented yet).  Using an exclamation mark causes the next result to be printed on a new line.  Ending the _print list_ with a semicolon or comma causes the cursor to remain on the same line, so that the next PRINT statement not start on a new line.

### Example

```
PRINT "My mind is going"
    
   My mind is going

PRINT 10 * 100

   1000

First_Name$ := "Dave"
Last_Name$ := "Bowman"
PRINT First_Name$ + " " + Last_Name$

   Dave Bowman

PRINT First_Name$; Last_Name$

   DaveBowman

PRINT First_Name$ !! Last_Name$

   Dave

   Bowman
```

## REM

Insert a comment.

## Syntax

REM _comment_

## RENUMBER

Renumber the program lines.  Currently no arguments are supported, only the default option to renumber the entire program with the first line given the number 10, and all subsequent lines incremented by 10.

### Example

```
30 PRINT "Hello"
11 PRINT "Blah"
23 PRINT "Meh"
5 CLS

LIST
   5 CLS
   11 PRINT "Blah"
   23 PRINT "Meh"
   30 PRINT "Hello"

RENUMBER
LIST
   10 CLS
   20 PRINT "Blah"
   30 PRINT "Meh"
   40 PRINT "Hello"
```

## REPEAT ... UNTIL

Repeat a series of instructions until a condition is met.

### Syntax

REPEAT
:
Instructions
:
UNTIL _t_

### Example

```
10 REM Roll dice until we get 2 sixes
20 Throws% := 0
30 REPEAT
40   D1% := RND(6) : D2% := RND(6)
50   PRINT "Throw ", Throws%, ": ", D1%, "+", D2%
60   Throws% = Throws% + 1
70 UNTIL D1% = 6 AND D2% = 6
80 PRINT "We got 2 sixes after ", Throws%, " throws!"
```

## RND

Generate a random number, or re-seed the random number generator.  

### Syntax

RND(_e_)

### Remarks

Pass any negative number to re-seed.  To return random floating-point number pass 1.  To return a random integer up to a maximum value, pass the maximum value.

## RUN

Execute the stored program.  Running from a different line number is not yet implemented.

### Syntax

RUN

## SAVE

Save a stored program to a file.

### Syntax

SAVE _e$_

### Remarks

_e$_ must be a valid filename.  Wildcard characters are not allowed.  If the file already exists the user is prompted with a warning and asked if the operation should be aborted.  If _e$_ does not end in ".BAS" then ".BAS" will be added automatically.

## SET BORDER

Change the border colour.

### Syntax

SET BORDER _e_

### Example

```
SET BORDER 2
```

## SET COLOUR

Assign colours to the current pallete and/or set flashing colours and flash speed.  

### Syntax

SET COLOUR _e1_ TO _e2_[,_e3_,_e4_]

### Remarks

_e1_ is the number of the current pallete you want to set.  _e2_ indicates the value of the base colour to be assigned to _e1_.  The list of base colours is given below.  _e4_ indicates a second colour that will flash regularly with _e2_.  _e3_ specifies the flashing speed (0 no flash, 1 slow flash, 2 fast flash).

| Value of _e2_ or _e4_ | Colour |
| --------------------- | ------ |
| 0                     | Black |
| 1                     | Dark blue |
| 2                     | Dark red |
| 3                     | Purple |
| 4                     | Dark green |
| 5                     | Dark cyan |
| 6                     | Brown |
| 7                     | Light grey |
| 8                     | Dark grey |
| 9                     | Light blue |
| 10                    | Light red |
| 11                    | Magenta |
| 12                    | Light green |
| 13                    | Cyan |
| 14                    | Yellow |
| 15                    | White |

### Example

```
10 REM Write a flashing yellow warning message
20 REM on a dark grey background in hi-res mode
30 SET MODE 80
40 SET COLOUR 0 TO 8
50 SET COLOUR 1 TO 14, 2, 8
60 SET COLOUR 3 TO 0
70 SET PEN 1 : PRINT "WARNING - Imminent meltdown!"
80 SET PEN 2 : PRINT "Evacuate to at least 100 km distance immediately."
90 SET PEN 3 : PRINT "Good luck and have a nice day."
```

## SET CONFIG BOOT

This a new command only implemented in RM BASICx64.  It is used to enable or disable the RM Nimbus "Welcome" boot sequence when RM BASICx64 starts.

### Syntax

SET CONFIG BOOT t

### Example

```
SET CONFIG BOOT TRUE
```

## SET CURPOS

Move the cursor to a specific position.

### Syntax

SET CURPOS _e1, _e2_

### Remarks

_e1_ is the column number and _e2_ is the row number to move the cursor to.

## SET DEG

Set the angle measurement unit to degrees.  Note that this is equivalent to [SET RAD](#set-rad) which sets the angle measurement to radians.

### Syntax

SET DEG _t_

### Example

```
SET DEG TRUE
```

## SET MODE

Change the screen mode between high-resolution, 4-colour mode (80) and low-resolution, 16-colour mode (40)

### Syntax

SET MODE _e_

### Example 

```
SET MODE 40
SET MODE 80
```

## SET PAPER

Change the paper colour.

### Syntax

SET PAPER _e_

### Example

```
SET PAPER 1
```

## SET PEN

Change the pen colour.

### Syntax

SET PEN _e_

### Example

```
SET PEN 2
```

## SET RAD

Set the angle measurement unit to radians.  Note that this is equivalent to [SET DEG](#set-rad) which sets the angle measurement to degrees.

### Syntax

SET RAD _t_

### Example

```
SET RAD TRUE
```

## SIN

Calculate the sine of an angle. The unit of the measurement for the angle can be set with [SET DEG](#set-deg) or [SET RAD](#set-rad).

### Syntax

SIN(_e_)

### Example

```
SET DEG TRUE
PRINT SIN(90)

   1

```

## SQR

Calculate the square root of a number.

### Syntax

SQR(_e_)

### Example

```
PRINT SQR(23)

   4.795831523312719

```

## TAN

Calculate the tangent of an angle. The unit of the measurement for the angle can be set with [SET DEG](#set-deg) or [SET RAD](#set-rad).

### Syntax

TAN(_e_)

### Example

```
```

## XOR

Bitwise XOR on two expressions.

### Syntax

_e1_ XOR _e2_