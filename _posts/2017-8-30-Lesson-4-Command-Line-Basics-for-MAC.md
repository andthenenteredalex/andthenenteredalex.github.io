---
published: false
categories: ['command line']
---

### Lesson 4

### The Basics of the Command Line on a Mac


Hello! 

This is where things are going to start getting more complicated. Now that you are used to running the commands mkdir, cd and ls, you can learn how to make these commands more useful by giving the computer more specific instructions. It is possible to make a directory in a different location, list the contents of a different directory, and change directories more efficiently.

Review:

Last lesson you used `mkdir` to make a new dirctory located in your current directory, `ls` to list the contents of your current directory, and `cd` to change your directory. You did specify which directory to change to and what to title each new directory, but there's more. `cd ~` changed to the home directory, and `cd..` took you back (to the left) one directory. 

You can modify a command to do something more complicated, such as changing to a completely different directory, or specifying somewhere else to make a directory, and so on. *These modifications are called arguments*.

Type this exactly from your terminal home page: 

```
mkdir fun/cat
mkdir fun/dog
mkdir fun/porcupine
mkdir fun/capybara
```

You just made the directories "cat", "dog", "porcupine" and "capybara" from the "~" location but told the computer to make the directories inside "fun" instead of your current location. 

Run this: `mkdir fun/cat/cat` , then `mkdir fun/cat/dog` , then `mkdir fun/cat/porcupine` .

This time the new directories "cat", "dog" and "porcupine" were created inside the "cat" directort which is inside "fun". See how this works? 

Using the `/` character (forward slash) instructs the computer exactly where to make the directory.  

This `/` character works for other commands too.

Run `ls fun/cat` to list the contents of the cat directory.  

Run `cd fun/cat` to change the directory to "cat".

Run `cd .. ` to get back to "fun", then `cd ..` to get back to " ~ ".

# Practice exercises:

```
mkdir fun/cat/cat/cat
mkdir fun/cat/cat/dog
mkdir fun/cat/cat/kitty
mkdir fun/cat/cat/porcupine
```

`ls fun/cat/cat` Then `cd fun/cat/cat`

From there, run `cd ~/fun/fun/fun` . Then `pwd` , then `cd ~/Documents` , `ls` , then `cd ~` . 


Remember to `pwd` to see where you are. This is when `pwd` is helpful, since it can get confusing navigating all these directories with only the text in Terminal. `pwd` helps you take a step back and see where you are.   

To visualize all of this, you can open the window in your finder again. Click your Desktop, click the Go in the top bar, click on Home roughly halfway down. This opens the window. 



Keep practicing, it's really complicated at first, but it gets easier.

