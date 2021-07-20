---
layout: default
title: Releases
nav_order: 4
---

# Releases

---

## 0.01B

21st July 2021

LOAD, SAVE, RUN commands implemented with minimal functionality.  EDIT and AUTO commands not yet implemented but program lines can be added or edited by typing the line number followed by the instruction(s), e.g. `10 SET MODE 40 : PRINT "Hi there!"`

IF...THEN...ELSE implemented.

Logical operators are not all bitwise, consistent with RM Basic.

See the [Reference](reference.html) for an up-to-date list of implemented commands.

## 0.01A

19th July 2021

This is a preliminary release just so you can get a snifter of things to come.  The reason for
doing this is simply due to the amount of effort that has gone in to getting the project this
far and not really having anything to show for it.

Development work has been in three slightly overlapping phases: 1. Building an emulation of the Nimbus text and graphics drivers, 2. Building an extendable parser to support RM Basic, and 3. Implementing RM Basic in the parser according to the RM Basic manual.  The past 18 months have been spent on phases 1 and 2.  Despite that being a fair chunk of work, there's actually almost nothing to share beyond screen shots because it's all "under-the-bonnet stuff".  

So in this release, you can try some simple commands and evaluate some not-so-simple expressions
and even experience some unspecific syntax errors!

See the [Reference](reference.html) for an up-to-date list of implemented commands.