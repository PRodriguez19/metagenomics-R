---
title: "Installing R packages"
teaching: 15
exercises: 10
questions:
- "How can I install packages in R?"
objectives:
- "Install and use libraries in R."
keypoints:
- "The library `ggplot2` creates plots that help/remarks the data analysis."
- "Libraries in R allow us to have sets of functions specialized in a global purpose."
math: true
---

## R packages

R contains tens of thousands of functions, objects, and help pages. But to save memory, R does not load every function, or object, or help page every time you start R. Instead, R loads only a core set known as Base R. 


### What is Base R?
  
This is a collection of R functions that gets loaded every time you start R. These functions provide the basics of the language, and you don't have to load a 

Comprehensively, these are called **Packages**. There are 10,000+ user contributed packages and this is still growing.

You can check what libraries are loaded in your current R session by typing into the console:

~~~
sessionInfo() #Print version information about R, the OS and attached or loaded packages

# OR

search() #Gives a list of attached packages
~~~
{: .language-r}


To use additional packages will require installation. Many packages can be installed from the [CRAN](http://cran.r-project.org/) or [Bioconductor](https://www.bioconductor.org/) repositories.

> ### Helpful tips for package installations
> * Package names are case sensitive!
> * At any point (especially if you’ve used R/Bioconductor in the past), in the console R may ask you if you want to **"update any old packages by asking Update all/some/none? [a/s/n]:". If you see this, type "a" at the prompt and hit Enter** to update any old packages. _Updating packages can sometimes take awhile to run._ If you are short on time, you can choose "n" and proceed. Without updating, you run the risk of conflicts between your old packages and the ones from your updated R version later down the road. 
> * If you see a message in your console along the lines of “binary version available but the source version is later”, followed by a question, **“Do you want to install from sources the package which needs compilation? y/n”, type n for no, and hit enter.**


## Package installation from CRAN 

CRAN is a repository where the latest downloads of R (and legacy versions) are found in addition to source code for thousands of different user contributed R packages.

<a href="{{ page.root }}/fig/cran_packages.png" >
  <img src="{{ page.root }}/fig/cran_packages.png" alt="cran_packages"  width="600" />
</a>

Packages for R can be installed from the [CRAN](http://cran.r-project.org/) package repository using the `install.packages` function. This function will download the source code from on the CRAN mirrors and install the package (and any dependencies) locally on your computer. 

An example is given below for the `ggplot2` package that will be required for some plots we will create later on. Run this code to install `ggplot2`.


~~~
#install.packages("ggplot2")
~~~
{: .language-r}


### Package installation from Bioconductor
Alternatively, packages can also be installed from [Bioconductor](https://www.bioconductor.org/), another repository of packages which provides tools for the analysis and comprehension of high-throughput **genomic data**. These packages includes (but is not limited to) tools for performing statistical analysis, annotation packages, and accessing public datasets.

<a href="{{ page.root }}/fig/bioconductor_logo.png" >
  <img src="{{ page.root }}/fig/bioconductor_logo.png" alt="bioconductor_logo"  width="300" />
</a>


There are many packages that are available in CRAN and Bioconductor, but there are also packages that are specific to one repository. Generally, you can find out this information with a Google search or by trial and error. 

To install from Bioconductor, you will first need to install BiocManager. *This only needs to be done once ever for your R installation.* 
Note that in the code below we are using Bioconductor to then install phyloseq using the `install()` function. 

~~~
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install("phyloseq")
~~~
{: .language-r}

> The code above may not be familiar to you - it is essentially using a new operator, a double colon `::` to execute a function from a particular package. This is the syntax: `package::function_name()`. 

### Loading libraries
Once you have the package installed, you can **load the library** into your R session for use. Any of the functions that are specific to that package will be available for you to use by simply calling the function as you would for any of the base functions. *Note that quotations are not required here.*


```r
library(ggplot2)
```

You can also check what is loaded in your current environment by using `sessionInfo()` and you should see your package listed as:

```r
other attached packages:
[1] ggplot2_2.0.0
```

In this case there are several other packages that were also loaded along with `ggplot2`.

Remember you only need to install a package once in R/RStudio. 

**However, to use the package, you will need to load the library every time we start a new R/RStudio environment.**

You can think of this as **installing a bulb** versus **turning on the light**. 

<a href="{{ page.root }}/fig/install_vs_library.jpeg" >
  <img src="{{ page.root }}/fig/install_vs_library.jpeg" alt="install_vs_library"  width="600" />
</a>


*Analogy and image credit to [Dianne Cook](https://twitter.com/visnut/status/1248087845589274624) of [Monash University](https://www.monash.edu/).* 

### Finding functions specific to a package

This is your first time using `ggplot2`, how do you know where to start and what functions are available to you? One way to do this, is by using the `Package` tab in RStudio. If you click on the tab, you will see listed all packages that you have installed. For those *libraries that you have loaded*, you will see a blue checkmark in the box next to it. Scroll down to `ggplot2` in your list:

<a href="{{ page.root }}/fig/ggplot_help.png" >
  <img src="{{ page.root }}/fig/ggplot_help.png" alt="ggplot_help"  width="300" />
</a>


If your library is successfully loaded you will see the box checked, as in the screenshot above. Now, if you click on `ggplot2` RStudio will open up the help pages and you can scroll through.

An alternative is to find the help manual online, which can be less technical and sometimes easier to follow. For example, [this website](https://ggplot2.tidyverse.org/reference/index.html) is much more comprehensive for ggplot2 and is the result of a Google search. Many of the Bioconductor packages also have very helpful vignettes that include comprehensive tutorials with mock data that you can work with.

If you can't find what you are looking for, you can use the [rdocumention.org](https://www.rdocumentation.org/) website that search through the help files across all packages available.


