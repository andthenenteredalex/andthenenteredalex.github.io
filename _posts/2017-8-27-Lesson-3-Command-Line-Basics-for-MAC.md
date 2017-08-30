---
published: true
categories: ['command line']
---

### Lesson 3

#### Command Line Basics for MAC

Switching between directories and listing directories. 

In Terminal, enter the following commands:

`mkdir zoo` , `mkdir "zoo zop"` , `mkdir "zad zad"` , `mkdir zad` .

We are reviewing how to make and name directories that you learned last lesson.

You can visualize your computer’s “home” by opening it in the finder. Click your desktop background to the side of your Terminal window. In the bar located at the top of your screen is a list of finder menus. From left to right, you should see an Apple, File, Edit, View, Go, Window, and Help. Select the Go menu and move your arrow down to Home and click on Home.

The window that opens is your home page. This is your computer’s starting point. `~` The one we visualized in lesson one. Here you can see via your user interface everything that is located in the Home directory. The Applications folder, Desktop, Documents, Downloads, Movies, Music, Pictures, Public, and all of the directories we made with our `mkdir` command. 

Last lesson you changed directories with the command `cd` to the “fun” directory. That command, because you were in the home directory, moved from home, or `~` , to “fun”. 

Go back to Terminal, and run the command `ls` . This lists the contents of whatever directory you are currently in. The information listed when `ls` is entered should be the same as the directories you see when you are looking at your Home window in the Finder.

Running `ls` alone lists the contents of whatever directory you are currently in. But you can modify a command to do something else.  This kind of modification to the basic command is called an **argument**. If you run the command `ls fun` , the computer lists the contents of the directory “fun”, even though you aren’t in “fun”.

Run `cd fun` . `mkdir fun` . `cd fun` . `mkdir fun` . `cd fun` . `mkdir fun` . `cd fun` . 

`pwd` .


You should have gotten this. 
```
AlexandersMBP2:fun alexclark$ pwd
/Users/alexanderclark/fun/fun/fun/fun
AlexandersMBP2:fun alexclark$
```


`Users/yourname/fun/fun/fun/fun`

The number of funs should match the number of funs you have created in total, including the one where you started.

This is how `cd` and `ls` work. Left to right.

`cd` always moves to the right unless the command has been modified. You can run the `cd` command until you run out of directories to the right to change to. How do move to the left? `cd ..` moves back, or to the left, one directory. 

`cd ~`  takes you all the way back home if you are somewhere else.

Thanks for reading lesson 3. I'll be back soon with lesson 4. 
