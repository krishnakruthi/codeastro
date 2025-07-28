# Debugging

![Top panel: That was the worst bug I've ever written. Bottom panel: That was the worst bug you've ever written so far.](imgs/debug_meme.png)

## Debugging Demo
The `debug_matrix.py` code is supposed to generate some pixel art but it currently crashes. We will use it to demonstrate the VS Code deubgger and fix the code. We have already set up our VS Code for python debugging, but you may need to follow the instructions in the activity below before you can run the VS Code debugger on this code. 

## Activity: Debug orbitize!

The issue you are tasked with investigating is this one: https://github.com/sblunt/orbitize/issues/230. 

### (If necessary): install development version of orbitize!:
To do so, download a development version of orbitize! for the debugging activity. You may have already done this already as part of Day0 setup, if you followed the installation instructions. If you did, you can skip this section. 

    git clone https://github.com/sblunt/orbitize.git

Next, we'll want to override your system's default `orbitize!` installation with this one. Install `orbitize!` from source by `cd`-ing into this repo you just cloned (there should be a requirements.txt file) and running:

    pip install -r requirements.txt -e .

That command just ran pip to install the package in the current directory, and to automatically update when you make changes to the code (useful for developing on packages). Installing code from source like this also allows you to use the interactive debugger in VS Code on the `orbitize!` source code by default. 

### Setup VS Code Debugger

To get the VS Code debugger set up to run the `broken_orbitize.py` script that reproduces the bug, open up the `broken_orbitize.py` file first. After opening the file, check in the bottom left corner of VS Code that you are in the `codeastro` Python environment. If not, click on the python environment (area circled below) to switch environments:

![What you should see in the VS Code status bar. Click on it to change environments.](imgs/debug_environment.png "You should see something like this.")

Then open the debug tab from the left side (4th buttom from top). Click the "create a launch.json file" link shown in the screenshot below:

![What you should see when you open up the debug tab](imgs/debug_new.png "You should see something like this.")

When you click it, a new .json file should be created. There should be a buttom in the bottom right of the text editor window that says "Add configuration...". When you click it, a dropdown link should appear to ask you what kind of debugging you would like to do, and select "Python File":

![Selecting debug mode](imgs/debug_selection.png "Select Python File")

This should create a file `.vscode/launch.json` in the base directory, with default settings for debugging a Python file. We are now almost ready, but I suggest adding the following line inside the configurations list:

    "cwd": "${fileDirname}"

This makes it so that the current working directory of the debugger will always be the directory that the Python file you are debugging is located in. To check you set it all up correctly, it should look nearly identical to the `demo_launch.json` file in the Day2 folder. 

Now that you are set up, use the VS Code debugger to try to identify which input(s) is/are causing the function to return NaN, and if you have time, suggest a fix. Use this as an opportunity to get familiar with using the interactive controls (step into, and step over) and/or breakpoints!

If you aren't able to step into `calc_orbit()`, you may need to add the following line to your launch.json file:

     "justMyCode": false

### Instructions

  * Follow the instructions above to set up the debugger on your machine and use it on the `broken_orbitize.py` script
  * Reproduce the error: run the code and verify the assertion in the script fails
  * Identify which of the nine inputs is/are causing the function to return NaN
    * step into the `calc_orbit` function
    * identify the line when NaNs first start appearing
    * what variable needs to be changed on this line to prevent the NaNs from being created?
  * (Optional) Modify the code to prevent this from happening in the future

### End Product
Report on Piazza the follow two items:
  * In what line of `orbitize!` do NaNs first start appearing?
  * Which of the nine inputs is/are cuasing the function to return NaN, and report on any modifications you made

### Roles
  * Driver: in charge of sharing their screen and typing the code for this activity
  * Navigator: in charge of directing the driver what to code (everyone else; can be more than one person)

## Debugging Principles

There is no one recipe for debugging. However, here are some general tips for debugging that you might find useful

  * If you have no idea what is broken, establish what is working and try to use process of elimination.
  * A good process of elimination method is binary search: see if it is the first half of the code that is breaking things, or the second half. If it's the first half, then check the first quarter vs the second quarter. Keep repeating and isolating the error this way.
  * Google error messages, especially if they are specific, to see if anyone else has hints or leads. However, do think about what commands they are suggesting you type, and don't blindly type them!
  * Learn to use interactive debuggers like the one in VS Code, which allows you to step through code line by line and stop at places of intereset. It is really useful when you have a lot of lines of code to sift through.  
  * Write tests for your function as you are writing the function so you can use them to debug your code (this is called test-driven development). It will also help clarify to yourself what exactly each function should do. 
  * Keep at it! You will develop an intuition for debugging as you do more of it. 
