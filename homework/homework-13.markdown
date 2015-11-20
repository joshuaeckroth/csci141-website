---
title: Homework 13
layout: default
---

Skills needed to complete this assignment:

- [Swing](/lecture/swing.html)
- [Exceptions](/lecture/exceptions.html)
- [Files](/lecture/files.html)

## Task 1

Create a "database editor" that shows a table with rows of records, a new record button, a delete record button, and a save and load records (to/from a file) buttons.

![Database](/images/database-1.png)

You can create your own database (e.g., sports scores, pokedex, etc.). You are required to have at least three columns, at least one of which is numeric.

Clicking "New Record" creates a new row. You can edit the contents of the rows by double-clicking a cell. "Delete Record" removes the selected row.

The "Load Records" button shows a file selector dialog and opens the chosen file. The contents of the file replace the contents of the table. The "Save Records" button saves the current contents of the table to the selected file. You choose how to read and store table data in the file.

## Extra credit

Create a menu bar that has a "File" menu with load, save, and quit actions, and a "Record" menu with new and delete record actions.

## More extra credit

Allow sorting the rows by clicking a column. Click a column twice to sort in the reverse order.

## More extra credit

Support adding/removing columns.
