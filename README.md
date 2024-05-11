# streaming-02-multiple-processes

> Multiple processes accessing a shared resource concurrently

## Overview

This example starts a shared database and multiple processes.

The processes represent multiple users, or locations, or programs
hitting a shared database at the same time.

## Prerequisites

1. Git
1. Python 3.7+ (3.11+ preferred)
1. VS Code Editor
1. VS Code Extension: Python (by Microsoft)

## Task 1. Fork

Fork this repository ("repo") into **your** GitHub account.

## Task 2. Clone

Clone **your** new GitHub repo down to the Documents folder on your local machine.

## Task 3. Explore

Explore your new project repo in VS Code on your local machine.

## Task 4. Execute Check Script

Execute 00_check_core.py to generate useful information.

## Task 5. Execute Multiple Processes Project Script

Execute multiple_processes.py.

Read the output. Read the code.
Try to figure out what's going on.

1. What libraries did we import?
   datetime, logging, multiprocessing, os, platform, sqlite3, sys, time
2. Where do we set the TASK_DURATION_SECONDS?
   Following the import of the libraries that are being used we set the TASK_DURATION_SECONDS along with any other program constants
3. How many functions are defined?
   There are seven functions
4. What are the function names?
   recreate_database
   create_table
   drop_table
   insert_pet
   process_one
   process_two
   process_three
5. In general, what does each function do?
   recreate_database
   Drops and recreates the database
   create_table
   Creates a table in the database
   drop_table
   Drops the table if it exists
   insert_pet
   Inserts a pet into pets table
   process_one
   Specifies name and breed of pet to add for process one
   process_two
   Specifies name and breed of pet to add for process two
   process_three
   Specifies name and breed of pet to add for process three
6. Where does the execution begin? Hint: generally at the end of the file.
   Line 169: if **name** == "**main**":
7. How many processes do we start?
   Three processes are started using multiprocessing.Process()
8. How many records does each process insert?
   There are two pets inserted into the database by each process

In this first run, we start 3 processes,
each inserting 2 records into a shared database
(for a total of 6 records inserted.)

In each case, the process gets a connection to the database,
and a cursor to execute SQL statements.
It inserts a record, and exits the database quickly.

In general, we're successful and six new records get inserted.

## Task 6. Execute Multiple Processes Script with Longer Tasks

For the second run, modify the task duration to make each task take 3 seconds.
Hint: Look for the TODO.
Run the script again.
With the longer tasks, we now get into trouble -
one process will have the database open and be working on it -
then when another process tries to do the same, it can't and
we end up with errors.

## Task 7. Document Results After Each Run

To clear the terminal, in the terminal window, type clear and hit enter or return.

`clear`

To document results, clear the terminal, run the script, and paste all of the terminal contents into the output file.

Use out0.txt to document the first run.

Use out3.txt to document the second run.

---

## Helpful Information

To get more help on the early tasks, see [streaming-01-getting-started](https://github.com/denisecase/streaming-01-getting-started).

### Select All, Copy, Paste

On Windows the select all, copy, paste hotkeys are:

- CTRL a
- CTRL c
- CTRL v

On a Mac the select all, copy, paste hotkeys are:

- Command a
- Command c
- Command v

Detailed copy/paste instructions (as needed)

1. To use these keys to transfer your output into a file,
   clear the terminal, run the script, then click in the terminal to make it active.
1. To select all terminal content, hold CTRL and the 'a' key together.
1. To copy the selected content, hold CTRL and the 'c' key together.
1. To paste, open the destination file (e.g. out0.py) for editing.
1. Click somewhere in the destination file to make it the active window.
1. Now hit CTRL a (both together) to select all of the destination file.
1. Hit CTRL v (both together) to paste the content from your clipboard.

Do a web search to find helpful videos on anything that seems confusing
and share them in our discussion.

### Reading Error Messages

Python has pretty helpful error messages.
When you get an error, read them carefully.

- What error do you get?

### Database Is Locked Error

Do a web search on the sqlite3 'database is locked' error.

- What do you learn?
- Once a process fails, it crashes the main process and everything stops.

### Deadlock

Deadlock is a special kind of locking issue where a process
is waiting on a resource or process, that is waiting also.

Rather than crashing, a system in deadlock may wait indefinitely,
with no process able to move forward and make progress.

### Learn More

Check out Wikipedia's article on deadlock and other sources to learn how to prevent and avoid locking issues in concurrent processes.
