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

_t_
a numeric expression that is evaluated; a non-zero value returns TRUE and 0 returns FALSE (at the moment RM BASICx64 expects a straight boolean type)

## ABS

Calculate the absolute value of a number.

### Syntax

ABS(_e_)

### Example

```
PRINT ABS(-1.2345)

   1.2345

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

## EXP

Calculate the exponential function, e^x

### Syntax

EXP(_e_)

### Example

```
PRINT EXP(1)

   2.718281828459045

```

## INT(_e_)

Calculate the largest whole number that is less than or equal to a given value.

### Example 

```
PRINT INT(34.9999)

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
```

## LN

Calculate the natural logarithm of a number.

### Syntax

LN(_e_)

### Example

```
PRINT LN(1.32)

   0.27763173659827955

```

## LOG

Calculate the logarithm to the base 10 of a number.

### Syntax

LOG(_e_)

### Example

```
PRINT LOG(5.2)

   0.7160033436347991

```

## PRINT

Prints a string or number on the screen.  RM Basic's PRINT command has a lot of flexibility which is not yet implemented here.

### Syntax

PRINT _exp_

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
```

## RND

Generate a random number, or re-seed the random number generator.  Pass any negative number to re-seed.  To return random floating-point number pass 1.  To return a random integer up to a maximum value, pass the maximum value.

### Syntax

RND(_e_)

### Example

```

```

## SET BORDER

Change the border colour.


### Syntax

SET BORDER _e_

### Example

```
SET BORDER 2
```

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