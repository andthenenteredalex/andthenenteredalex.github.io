---
published: false
categories: ['command line']
---

### Lesson 2

#### Command Line Basics for Mac


In this lesson you will learn how to create directories and switch between directories. 


Review: What’s a directory? What command did you learn last time?



Open Terminal. Type `mkdir fun` and hit enter to run the command.

Did anything happen? It doesn’t look like it based on your terminal window, but your computer made a directory titled "fun". The command `mkdir` means **m**a**k**e a **dir**ectory. Pretty simple, right?

We know that a directory “fun” exists because we just made it. Now enter the command `cd fun` . `cd` is the command to **c**hange **dir**ectories . We specified that we wished to change to the "fun" directory when we said `cd fun` . 
 
We just changed directories. We are now in the directory titled “fun”. As we learned last lesson, the computer always tells us what directory we are in following the `:` in the information on the screen. Now instead of the `~` symbol, we see we are currently in "fun".

```
AlexandersMBP2:~ alexclark$ mkdir fun
AlexandersMBP2:~ alexclark$ cd fun
AlexandersMBP2:fun alexclark$ 
```

Run the `pwd` command and your computer will show you where you are.
```
AlexandersMBP2:fun alexclark$ pwd
/Users/alexanderclark/fun
AlexandersMBP2:fun alexclark$
```

When we ran the `mkdir` command from the home directory, any directory we made would be in the home directory. But now that we are in the `fun` directory, any directory we make will be in the `fun` directory.

Make a few more directories. Run the following commands: `mkdir dog` . `mkdir “big dog”` . To include a space in a directory name, use quotation marks on each side of the directory title.

Without quotation marks, the computer makes multiple directories with a single command, each word being assigned to its own directory.

Run the following commands: `mkdir cat fish` . Then `mkdir “cat fish”` with the quoatation marks. We made two directories in the first command, `cat` and `fish` , and then one titled `“cat fish”` in the second.

You just learned how to **m**a**k**e and **c**hange **dir**ectories!

This lesson covered making directories with the command `mkdir` , and changing directories with the command `cd` . Make a few more directories in the fun directory so you get the hang of the process. 

If you're lost, don't worry at all. We'll be spending more time `cd` -ing and `mkdir` -ing in the next lesson, I just wanted to introduce you to those commands before covering them more detail.

See you in ## Lesson 3.
