---
published: false
---

#### The Very Basics of the Command Line on a Mac
### Lesson 2

Lesson 2

In this lesson we will be creating a directories and switching between directories. 

Review: What’s a directory? What command did we learn last time?
Open Terminal. Type `mkdir fun` and hit enter to run the command.

Did anything happen? It doesn’t look like it based on your terminal window, but your computer just made a directory titled fun. The command `mkdir` means **m**a**k**e **dir**ectory. Pretty simple right?

We know that a directory “fun” exists, because we just made it. Now enter the command `cd fun` .
 
We just changed directories. We are now in the directory titled “fun”. As we learned last lesson, the computer always tells us what directory we are in following the `:` in the information on the screen. Now instead of the `~` symbol, we see we are currently in "fun".

```AlexandersMBP2:~ alexclark$ mkdir fun
AlexandersMBP2:~ alexclark$ cd fun
AlexandersMBP2:fun alexclark$ 
```

Run the `pwd` command and your computer will show you where you are.

When we ran the `mkdir` command from the home directory, any directory we made would be in the home directory. But now that we are in the `fun` directory, any directory we make will be in the `fun` directory.

Make a few more directories. Run the following commands: `mkdir dog` . `mkdir “big dog”` . To include a space in a directory name, use quotation marks on each side of the directory title.

Without quotation marks, the computer makes each word a separate directory with a single command.

Run the following commands: `mkdir cat fish` . Then `mkdir “cat fish”` . We made two directories in the first command, `cat` and `fish` , and then one titled `“cat fish”` in the second.

You just learned how to **m**a**k**e and **c**hange **dir**ectories!

Today’s lesson covered making directories, with the command `mkdir` ,and changing directories, with the command `cd` . Make a few more directories in the fun directory so you get the hang of the process. 

Check back later for ##lesson 3
