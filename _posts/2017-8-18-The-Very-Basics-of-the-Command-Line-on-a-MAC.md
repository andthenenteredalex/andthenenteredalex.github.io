

---
published: true
---

#### The Very Basics of the Command Line on a MAC

The command line is a method of communicating with your computer using only the keyboard, rather than with a mouse or trackpad. By typing commands directly into your computer, bypassing your Graphical User Interface (GUI), you are accomplishing what your computer is always doing behind the scenes.

There’s a reason that forms of code, such as HTML, Python, C++, etc., are all referred to as languages. Using a computer code language is just the action of communicating with your computer via a language it understands. Learning the language your computer speaks resembles learning any other language, the task requires memorization, and practical application. 

The computer requires input in a specific form, called a command, which must be exact, but, like a spoken human language, it can be translated to english correctly in multiple ways.The computer only does what you tell it to, nothing more, and nothing less. Using the command line is the action of communicating commands to your computer via its language.

This series will be comprised of many short hands-on lessons which I will be adding to on a regular basis. For now, only lesson 1 is available.  

#### Lesson 1

Understanding how the computer stores and communicates information to you is the first thing to learn, we will start by learning a simple command and analyzing the information that the computer shows us.

Since punctuation, spaces, and capitalization matter when typing commands, I will always leave an empty space on either side of a command that I type in this text so that you can see precisely what part of what I type is the command. I’ll also highlight it.

Terminal is the application we use for the command line. Spotlight search for Terminal. Open Terminal. 

Now that Terminal is open, let’s begin. Type `pwd` , no caps, no spaces, no punctuation. Just: `pwd` , then hit the return/enter key.  

The command `pwd` means **p**rint **w**orking **d**irectory. Print working directory is roughly translated “show me where we are.” Hitting enter after properly typing a command runs the command.

So where are we? Let’s figure out how to read the result. 

![lesson1 image](/Users/alexanderclark/Documents/Github/andthenenteredalex.github.io/images/lesson1image.png)

When I typed the command in my computer, this is exactly what Terminal showed me.

The `$` shows where the entry space begins, what we type to the right of the `$` is the command. That is why at the end of what printed after we ran the command, we see another `$` . 

The `AlexandersMBP2: ~ alexclark$` is not the command, nor is it the result. It is information which shows who the computer belongs to, `Alexanders`, and it’s a `MacBook Pro2`. The space directly to the right of the `:` shows which directory we are in, the directory is the word we use for location or folder, when we are using the command line. The `~` symbol means home, it refers to the home location of your computer, the starting point for any command. Lastly, the user is `alexclark`. Then the `$` at the end of `AlexandersMBP2:~ alexclark$` means that the space to the right is going to be another command, but it is empty because we haven’t typed another one yet.

So what did running the command `pwd` give us? The stuff in the line just beneath where we first typed. `/users/alexanderclark` .

That means we are at the starting point.  There is no back button from here, we are as far back as we can get. It’s like the home screen on an iPhone, any other location is a step away from home.

The takeaway for this first section, the `~` symbol means home, spaces, capitals, and punctuation matter in a command, a directory is a folder, and a folder is a location. There is a lot of information on the screen, but it all makes sense once we know how to interpret the letters and symbols.

To conclude lesson 1, run the `pwd` command a few more times by typing `pwd` and hitting the enter key without any spaces, capitals, or punctuation, just to make sure you know it.

Now you know how to find out where you are. This command works in any location, and actually makes sense after you have gone somewhere. Running it from the home screen does nothing but tell you that you are home, or `~` , as we say in the business.
