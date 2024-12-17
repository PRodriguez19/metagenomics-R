---
title: "First Steps on R"
teaching: 15
exercises: 10
questions:
- "What is R, and why is important to learn to use it?"
- "What types of data does the R language has?"

objectives:
- "Understand why R is important."
- "Describe the purpose and use of each panel in the RStudio IDE"
- "Locate buttons and options in the RStudio IDE"
- "Define a variable"
- "Assign data to a variable"

keypoints:
- "R is a programming language"
- "RStudio is a useful tool for script writing and data-management."
- "A variable can temporarily store data."
---


*It takes courage to sail in uncharted waters*
  -Snoopy

## Introduction to R/RStudio

### What is R?

“R” is used to name a programming language and the software that reads and interprets the instructions written on the scripts of this language. Is specialized in statistical computing and graphics. 

The R environment combines:

* effective handling of big data 
* collection of integrated tools
* graphical facilities
* simple and effective programming language

### Why use R?

<a href="{{ page.root }}/fig/why_R.png" >
  <img src="{{ page.root }}/fig/why_R.png" alt="R vs RStudio." width="600" />
</a>

R is a powerful environment. It has a wide range of statistics and general data analysis and visualization capabilities.

* Data handling, wrangling, and storage
* Wide array of statistical methods and graphical techniques available
* Easy to install on any platform and use (and it’s free!)
* Open source with a large and growing community of peers
* R produces high-quality graphics that are reproducible 

#### Example of R used in the media
* *"At the BBC data team, we have developed an R package and an R cookbook to make the process of creating publication-ready graphics in our in-house style..."* - [BBC Visual and Data Journalism cookbook for R graphics](https://bbc.github.io/rcookbook/)



### What is RStudio?

Here, we will use be using R via RStudio. First time users often confuse the two. At its simplest, R is like a car's engine while RStudio is like a car's dashboard as illustrated in the 
Figure below.


<a href="{{ page.root }}/fig/R_vs_RStudio_1.png" >
  <img src="{{ page.root }}/fig/R_vs_RStudio_1.png" alt="R vs RStudio." />
</a>

More precisely, R is a programming language that runs computations, while RStudio is a freely available open-source **integrated development environment (IDE)** that provides an interface by adding many convenient features and tools. So just as the way of having access to a speedometer, rearview mirrors, and a navigation system makes driving much easier, using RStudio's interface makes using R much easier as well. 

> RStudio provides an environment with many features to make using R easier and is a great alternative to working on R in the terminal. 

<a href="{{ page.root }}/fig/rstudio_logo.png" >
  <img src="{{ page.root }}/fig/rstudio_logo.png" alt="RStudio logo."  width="300" />
</a>

* Graphical user interface, not just a command prompt
* Great learning tool 
* Free for academic use
* Platform agnostic
* Open source

## Creating a new project directory in RStudio

Let's create a new project directory for our "Introduction to R" lesson today. 

1. Open RStudio
2. Go to the `File` menu and select `New Project`.
3. In the `New Project` window, choose `New Directory`. Then, choose `New Project`. Name your new directory `Intro-to-R` and then "Create the project as subdirectory of:" the root of your VACC home account (`~`).
4. Click on `Create Project`.
5. After your project is completed, if the project does not automatically open in RStudio, then go to the `File` menu, select `Open Project`, and choose `Intro-to-R.Rproj`.
6. When RStudio opens, you will see three panels in the window.
7. Go to the `File` menu and select `New File`, and select `R Script`. 
8. Go to the `File` menu and select `Save As...`, type `Intro-to-R.R` and select `Save`

The RStudio interface should now look like the screenshot below.

<a href="{{ page.root }}/fig/Rstudio_interface.png" >
  <img src="{{ page.root }}/fig/Rstudio_interface.png" alt="RStudio interface."  width="800" />
</a>


### What is a project in RStudio?

It is simply a directory that contains everything related your analyses for a specific project. RStudio projects are useful when you are working on context- specific analyses and you wish to keep them separate. When creating a project in RStudio you associate it with a working directory of your choice (either an existing one, or a new one). A `. RProj file` is created within that directory and that keeps track of your command history and variables in the environment. The `.RProj file` can be used to open the project in its current state but at a later date.

When a project is **(re) opened** within RStudio the following actions are taken:
 
* A new R session (process) is started
* The .RData file in the project's main directory is loaded, populating the environment with any objects that were present when the project was closed. 
* The .Rhistory file in the project's main directory is loaded into the RStudio History pane (and used for Console Up/Down arrow command history).
* The current working directory is set to the project directory.
* Previously edited source documents are restored into editor tabs
* Other RStudio settings (e.g. active tabs, splitter positions, etc.) are restored to where they were the last time the project was closed.

*Information adapted from [RStudio Support Site](https://support.rstudio.com/hc/en-us/articles/200526207-Using-Projects)*


## Organizing your working directory & setting up

### RStudio Interface

**The RStudio interface has four main panels:**

1. **Console**: where you can type commands and see output. *The console is all you would see if you ran R in the command line without RStudio.*
2. **Script editor**: where you can type out commands and save to file. You can also submit the commands to run in the console.
3. **Environment/History**: environment shows all active objects and history keeps track of all commands run in console
4. **Files/Plots/Packages/Help** is a handy browser for your current files, this is where your plots will appear, you can view package information, and much more.

### Viewing your working directory

Before we organize our working directory, let's check to see where our current working directory is located by typing into the console:

~~~
getwd() # return an abolute filepath
# this is also our first example of a function 
~~~
{: .language-r}


Your working directory should be the `Intro-to-R` folder constructed when you created the project. The working directory is where RStudio will automatically look for any files you bring in and where it will automatically save any files you create, unless otherwise specified. 

You can visualize your working directory by selecting the `Files` tab from the **Files/Plots/Packages/Help** window. 

<a href="{{ page.root }}/fig/Get_wd.png" >
  <img src="{{ page.root }}/fig/Get_wd.png" alt="getwd."  width="400" />
</a>


If you wanted to choose a different directory to be your working directory, you could navigate to a different folder in the `Files` tab, then, click on the `More` dropdown menu which appears as a Cog and select `Set As Working Directory`.

<a href="{{ page.root }}/fig/Set_wd.png" >
  <img src="{{ page.root }}/fig/Set_wd.png" alt="setwd."  width="400" />
</a>
 

### Structuring your working directory

To organize your working directory for a particular analysis, you should separate the original data (raw data) from intermediate datasets. For instance, you may want to create a `data/` directory within your working directory that stores the raw data, and have a `results/` directory for intermediate datasets and a `figures/` directory for the plots you will generate.

Let's create these three directories within your working directory by clicking on `New Folder` within the `Files` tab. 

When finished, your working directory should look like:

<a href="{{ page.root }}/fig/complete_wd_setup.png" >
  <img src="{{ page.root }}/fig/complete_wd_setup.png" alt="Complete_wd_setup."  width="400" />
</a>


### Setting up 

This is more of a housekeeping task. In the future, we may be writing long lines of code in our script editor and want to make sure that the lines "wrap" and you don't have to scroll back and forth to look at your long line of code.

Click on Code -> Soft Wrap Long lines (make sure this is checked off)

## Interacting with R

Now that we have our interface and directory structure set up, let's start playing with R! There are **two main ways** of interacting with R in RStudio: using the **console** or by using **script editor** (plain text files that contain your code).

### Console window

The **console window** (in RStudio, the bottom left panel) is the place where R is waiting for you to tell it what to do, and where it will show the results of a command.  You can type commands directly into the console, but they will be forgotten when you close the session. 

Let's test it out:

~~~
3 + 5
~~~
{: .language-r}


<a href="{{ page.root }}/fig/console.png" >
  <img src="{{ page.root }}/fig/console.png" alt="Console."  width="400" />
</a>

### Script editor

Best practice is to enter the commands in the **script editor**, and save the script. You are encouraged to comment liberally to describe the commands you are running using `#`. This way, you have a complete record of what you did, you can easily show others how you did it and you can do it again later on if needed. 

**The Rstudio script editor allows you to 'send' the current line or the currently highlighted text to the R console by clicking on the `Run` button in the upper-right hand corner of the script editor**. 

Now let's try entering commands to the **script editor** and using the comments character `#` to add descriptions and highlighting the text to run:
	
	# Intro to R Lesson
	# Feb 16th, 2016

	# Interacting with R
	
	## I am adding 3 and 5. R is fun!
	3+5


Alternatively, you can run by simply pressing the `Ctrl` and `Return/Enter` keys at the same time as a shortcut.

You should see the command run in the console and output the result.

<a href="{{ page.root }}/fig/script_editor_output.png" >
  <img src="{{ page.root }}/fig/script_editor_output.png" alt="script editor."  width="300" />
</a>

	
What happens if we do that same command without the comment symbol `#`? Re-run the command after removing the # sign in the front:

~~~
I am adding 3 and 5. R is fun!
3+5
~~~
{: .language-r}


Now R is trying to run that sentence as a command, and it 
doesn't work. We get an error in the console *"Error: unexpected symbol in "I am" means that the R interpreter did not know what to do with that command."*

***

## Console command prompt

Interpreting the command prompt can help understand when R is ready to accept commands. Below lists the different states of the command prompt and how you can exit a command:

**Console is ready to accept commands**: `>`.

If R is ready to accept commands, the R console shows a `>` prompt. 

When the console receives a command (by directly typing into the console or running from the script editor (`Ctrl-Enter`), R will try to execute it.

After running, the console will show the results and come back with a new `>` prompt to wait for new commands.


**Console is waiting for you to enter more data**: `+`.

If R is still waiting for you to enter more data because it isn't complete yet,
the console will show a `+` prompt. It means that you haven't finished entering
a complete command. Often this can be due to you having not 'closed' a parenthesis or quotation. 

**Escaping a command and getting a new prompt**: `esc`

If you're in Rstudio and you can't figure out why your command isn't running, you can click inside the console window and press `esc` to escape the command and bring back a new prompt `>`.

### Keyboard shortcuts in RStudio
In addition to some of the shortcuts described earlier in this lesson, we have listed a few more that can be helpful as you work in RStudio.

| key              | action                 |
| ---------------- | ---------------------- |
| <kbd>Ctrl</kbd>+<kbd>Enter</kbd>     | Run command from script editor in console with Windows or Linux|
| <kbd>Command</kbd>+<kbd>Enter</kbd>     | Run command from script editor in console with MacOS |
| <kbd>ESC</kbd> | Escape the current command to return to the command prompt          |
| <kbd>Ctrl</kbd>+<kbd>1</kbd>      | Move cursor from console to script editor        |
| <kbd>Ctrl</kbd>+<kbd>2</kbd>     | Move cursor from script editor to console |
| <kbd>Tab</kbd>     | Use this key to complete a file path       |
| <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>C</kbd>     | Comment the block of highlighted text               |


> ## Exercise 
>
>Try highlighting only `3 +` from your script editor and running it. Find a way to bring back the command prompt `>` in the console.
{: .challenge} 


## The R syntax
Now that we know how to talk with R via the script editor or the console, we want to use R for something more than adding numbers. To do this, we need to know more about the R syntax. 


The main "parts of speech" in R (syntax) include:

  - the **comments** `#` and how they are used to document function and its content
  - **variables** and **functions**
  - the **assignment operator** `<-`

_NOTE: indentation and consistency in spacing is used to improve clarity and legibility_

We will go through each of these "parts of speech" in more detail, starting with the assignment operator.

### Assignment operator

To do useful and interesting things in R, we need to assign _values_ to
_variables_ using the assignment operator, `<-`.  For example, we can use the assignment operator to assign the value of `3` to `x` by executing:

~~~
x <- 3
~~~
{: .language-r}


The assignment operator (`<-`) assigns **values on the right** to **variables on the left**. 

*In RStudio, typing `Alt + -` (push `Alt` at the same time as the `-` key, on Mac type `option` and the `-` key) and this will write ` <- ` in a single keystroke.*


### Variables

A variable is a symbolic name for (or reference to) information. Variables in computer programming are analogous to "buckets", where information can be maintained and referenced. On the outside of the bucket is a name. When referring to the bucket, we use the name of the bucket, not the data stored in the bucket.

In the example above, we created a variable or a 'bucket' called `x`. Inside we put a value, `3`. 

Let's create another variable called `y` and give it a value of 5. 

~~~
y <- 5
~~~
{: .language-r}


When assigning a value to an variable, R does not print anything to the console. You can force to print the value by using parentheses or by typing the variable name.

~~~
y 
~~~
{: .language-r}


You can also view information on the variable by looking in your `Environment` window in the upper right-hand corner of the RStudio interface.

<a href="{{ page.root }}/fig/environment.png" >
  <img src="{{ page.root }}/fig/environment.png" alt="script editor."  width="200" />
</a>


Now we can reference these buckets by name to perform mathematical operations on the values contained within. What do you get in the console for the following operation: 

~~~
x + y
~~~
{: .language-r}


Try assigning the results of this operation to another variable called `number`. 

~~~
number <- x + y
~~~
{: .language-r}


> ## Exercises 
> 
> 1. Try changing the value of the variable `x` to 5. What happens to `number`?
> 
> 2. Now try changing the value of variable `y` to contain the value 10. What do you need to do, to update the variable `number`?
{: .challenge} 