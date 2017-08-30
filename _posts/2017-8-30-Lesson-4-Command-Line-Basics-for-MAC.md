---
published: false
categories: ['command line']
---

### Lesson 4

### The Basics of the Command Line on a Mac


Hello! 
This is where things are going to start getting more complicated. Now that you are used to running commands and can make, change and list the contents of directories, I'm going to explain how to give the computer more specific instructions which ultimatey allow us to cut out steps.

Review:

Last lesson we used `mkdir` to make a new dirctory located in our current directory, `ls` to list the contents of the current directory, and `cd` to change our directory. We did specify which directory to change to and what to title our new directory, but we didn't take it further]] farther]]? than that. `cd ~` changed to the home directory, and `cd..` took us back (to the left) one directory. 

We can modify a command to do something more complicated, such as changing to a completely different directory, or specifying somewhere else to make a directory, and so on. *This modification is called an argument*.

Type this exactly from your terminal home page: 

mkdir fun/cat
mkdir fun/dog
mkdir fun/porcupine
mkdir fun/capybara

You just made the directories "cat", "dog", "porcupine" and "capybara" from the ~ location but told the computer to make the directories inside fun instead of your current location. 

Run this: mkdir fun/cat/cat , then mkdir fun/cat/dog , then mkdir fun/cat/porcupine .

This time the new directories "cat" and "dog" are located within the "cat" directort which is inside "fun".

Using the / character (forward slash) instructs the computer exactly where to make the directory.  

This / character works for other commands too.

ls fun/cat lists the contents of the cat directory. 

cd fun/cat changes directories to cat.


Practice exercises:

mkdir fun/cat/cat/cat
mkdir fun/cat/cat/dog
mkdir fun/cat/cat/kitty
mkdir fun/cat/cat/porcupine

ls fun/cat/cat
cd fun/cat/cat

Remember to run pwd to see where you are. This is when pwd is helpful. It can get confusing navigating all these directories with only the text in Terminal, and pwd helps you take a step back and see where you are.   

To visualize this all, you can open the window in your finder again. Click desktop, click the Go in the top bar, click on Home roughly halfway down. This opens the window. 

Trom there, run cd ~/fun/fun/fun . Then pwd , cd ~/Documents

Keep practicing, it's really complicated at first, but it gets easier.

