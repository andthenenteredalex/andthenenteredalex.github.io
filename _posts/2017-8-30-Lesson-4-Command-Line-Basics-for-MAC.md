---
published: false
categories: ['command line']
---

### Lesson 4

### Command Line Basics for Mac


Hello! 

This is where things are going to start getting more complicated. Now that you are used to running the commands `mkdir`, `cd` and `ls`, you can learn how to make these commands more useful by giving the computer more specific instructions. It is possible to create a directory in a different location, list the contents of a different directory, and change directories more efficiently.

Review:

Last lesson you used `mkdir` to make a new dirctory located in your current directory, `ls` to list the contents of your current directory, and `cd` to change your directory. You did specify which directory to change to and what to title each new directory. `cd ~` changed to the home directory, and `cd..` took you back (to the left) one directory. 

You also can modify a command to do something more complicated, such as changing to a completely different directory, or specifying somewhere else to make a directory, and so on. As stated in the last lesson, *These modifications are called arguments*.

Type this exactly from your terminal home page: 

```
mkdir fun/cat
mkdir fun/dog
mkdir fun/porcupine
mkdir fun/capybara
```

Using the `/` key to specify where to create a new directory, you just made the directories "cat", "dog", "porcupine" and "capybara" from your "~" location, but created the directories inside "fun" *instead of your current location*. 

Run this: `mkdir fun/cat/cat` , then `mkdir fun/cat/dog` , then `mkdir fun/cat/porcupine` .

This time, the new directories "cat", "dog" and "porcupine" were created inside the "cat" directory, which is inside "fun". See how this works? 

Using the `/` character (forward slash) instructs the computer exactly where to make the directory.  

This `/` character works for other commands too.

Run `ls fun/cat` to list the contents of the "cat" directory.  

Run `cd fun/cat` to change to the "cat" directory, bypassing "fun".

Run `cd .. ` to get back to "fun", then `cd ..` to get back to " ~ ".

# Practice exercises:

From the home location, run: 
```
mkdir fun/cat/cat/cat
mkdir fun/cat/cat/dog
mkdir fun/cat/cat/kitty
mkdir fun/cat/cat/porcupine
```

```
ls fun/cat/cat  
cd fun/cat/cat
```

From there, run: `cd ~/fun/fun/fun` . Then `pwd` , then `cd ~/Documents` , `ls` , then `cd ~` . 


Remember to `pwd` to see where you are. This is when `pwd` is helpful, since it can get confusing navigating all these directories with only the text in Terminal. `pwd` helps you take a step back and see where you are.   

To visualize all of this, open the window in your finder by clicking your desktop, then clicking the Go in the top menu bar, click on Home roughly halfway down. This opens the window. 



Keep practicing, it's really complicated at first, but it gets easier.

