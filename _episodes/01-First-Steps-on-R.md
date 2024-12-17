---
title: "First Steps on R"
teaching: 10
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

## RStudio setup 

### What is R?

“R” is used to name a programming language and the software that reads and interprets the instructions written on the scripts of this language. Is specialized in statistical computing and graphics. 

The R environment combines:

* effective handling of big data 
* collection of integrated tools
* graphical facilities
* simple and effective programming language

### Why use R?

<a href="{{ page.root }}/fig/why_R.png" >
  <img src="{{ page.root }}/fig/why_R.png" alt="R vs RStudio." width="600" style="border: 2px solid grey"/>
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
  <img src="{{ page.root }}/fig/rstudio_logo.png" alt="RStudio logo."  width="20%" height="25%" />
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
  <img src="{{ page.root }}/fig/Rstudio_interface.png" alt="RStudio interface."  width="20%" height="25%" />
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

<a href="{{ page.root }}/fig/Complete_wd_setup.png" >
  <img src="{{ page.root }}/fig/Complete_wd_setup.png" alt="Complete_wd_setup."  width="400" />
</a>


#### Setting up 

This is more of a housekeeping task. In the future, we may be writing long lines of code in our script editor and want to make sure that the lines "wrap" and you don't have to scroll back and forth to look at your long line of code.

Click on Code -> Soft Wrap Long lines (make sure this is checked off)