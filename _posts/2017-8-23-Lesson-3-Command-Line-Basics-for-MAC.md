---
published: false
categories: ['command line']
---


### Lesson 3
Switching between directories, and listing directories. 
In Terminal, enter the following commands:

'mkdir funny' , 'mkdir bunny honey' , 'mkdir “bunny honey”' , 'mkdir “day night”' , 'mkdir zay zight' .


Now it is time to visualize where we are in the computer. Click your desktop background to the side of your Terminal window. In the top list of finder menus, from left to right, you should see an Apple, File, Edit, View, Go, Window, and Help. Select the Go menu and move your arrow down to Home and click on Home.

The window the opens is your home page. This is your computer’s starting point. The one we visualized in lesson one. Here we can see everything in the Home directory, the Applications folder, Pictures, Music, Movies, Documents, Downloads, and all of the directories we made with our mkdir command. 

Last lesson we changed directories with the command cd to the fun directory. That command, because we were in the home directory, moved us from home, or “~”, to “fun”. 

Go back to Terminal, and run the command ls . This lists the contents of whatever directory you are currently in. The information listed when ls is entered should be the same as the directories you see when you are looking at your Home window in the Finder.

Running ls alone lists the contents of whatever directory we are in. But we can modify a command to do something else.  This kind of modification to the basic command is called an argument. If you run the command ls fun , it lists the contents of the directory fun, even though we aren’t in “fun”.

Run cd fun . mkdir fun . cd fun . mkdir fun . cd fun . mkdir fun . cd fun . 

pwd .


'''You should have gotten this. 
AlexandersMBP2:fun alexclark$ pwd
/Users/alexanderclark/fun/fun/fun/fun
AlexandersMBP2:fun alexclark$
'''

The number of funs should match the number of funs you have created in total, including the one where we started.

this is how cd and ls work. left to right.
