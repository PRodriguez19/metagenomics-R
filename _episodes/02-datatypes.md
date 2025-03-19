---
title: "R Data Types"
teaching: 10
exercises: 5
questions:
- "What types of data does the R language have?"
objectives:
- "Learn the types of data that we can manage in R."
keypoints:
- "R uses different types of data to store information."
---

## Data Types

Variables can contain values of specific types within R. The six **data types** that R uses include: 

* `"numeric"` for any numerical value, including whole numbers and decimals. This is the most common data type for performing mathematical operations.
* `"character"` for text values, denoted by using quotes ("") around value. For instance, while 5 is a numeric value, if you were to put quotation marks around it, it would turn into a character value, and you could no longer use it for mathematical operations. Single or double quotes both work, as long as the same type is used at the beginning and end of the character value.
* `"integer"` for whole numbers (e.g., `2L`, the `L` indicates to R that it's an integer). It behaves similar to the `numeric` data type for most tasks or functions; however, it takes up less storage space than numeric data, so often tools will output integers if the data is known to be comprised of whole numbers. Just know that integers behave similarly to numeric values. If you wanted to create your own, you could do so by providing the whole number, followed by an upper-case L.
* `"logical"` for `TRUE` and `FALSE` (the Boolean data type). The `logical` data type can be specified using four values, `TRUE` in all capital letters, `FALSE` in all capital letters, a single capital `T` or a single capital `F`.
* `"complex"` to represent complex numbers with real and imaginary parts (e.g.,
  `1+4i`) and that's all we're going to say about them
* `"raw"` that we won't discuss further

The table below provides examples of each of the commonly used data types:

| Data Type  | Examples|
| -----------:|:-------------------------------:|
| Numeric:  | 1, 1.5, 20, pi|
| Character:  | “anytext”, “5”, “TRUE”|
| Logical:  | TRUE, FALSE, T, F|

The type of data will determine what you can do with it. For example, if you want to perform mathematical operations, then your data type cannot be character or logical. Whereas if you want to search for a word or pattern in your data, then you data should be of the character data type. The task or function being performed on the data will determine what type of data can be used. 


## Data Structures

## Vectors and data types

A vector is the most common and basic data type in R, and is pretty much the workhorse of R. A vector is composed by a series of values, such as numbers

<a href="{{ page.root }}/fig/vector2.png" >
  <img src="{{ page.root }}/fig/vector2.png" alt="vector2"  width="400" />
</a>

or characters,

<a href="{{ page.root }}/fig/vector1.png" >
  <img src="{{ page.root }}/fig/vector1.png" alt="vector1"  width="400" />
</a>

or logical values,

<a href="{{ page.root }}/fig/vector5-logical.png" >
  <img src="{{ page.root }}/fig/vector5-logical.png" alt="vector5"  width="400" />
</a>


We can assign a series of values to a vector using the `c()` function. For example we can create a vector of animal weights and assign it to a new object `weight_g`:

~~~
# Create a numeric vector and store the vector as a variable called 'weight_g'
weight_g <- c(50, 60, 65, 82)
weight_g
~~~
{: .language-r}

A vector can also contain characters:

~~~
molecules <- c("dna", "rna", "protein")
molecules
~~~
{: .language-r}

The quotes around "dna", "rna", etc. are essential here. Without the quotes R will assume there are objects called `dna`, `rna` and `protein`. As these objects don't exist in R's memory, there will be an error message.

There are many functions that allow you to inspect the content of a vector. `length()` tells you how many elements are in a particular vector:

~~~
length(weight_g)
length(molecules)
~~~
{: .language-r}

An important feature of a vector, is that all of the elements are the same type of data.  The function `class()` indicates the class (the type of element) of an object:

~~~
class(weight_g)
class(molecules)
~~~
{: .language-r}


The function `str()` provides an overview of the structure of an object and its elements. It is a useful function when working with large and complex objects:

~~~
str(weight_g)
str(molecules)
~~~
{: .language-r}


You can use the `c()` function to add other elements to your vector:

~~~
weight_g <- c(weight_g, 90) # add to the end of the vector
weight_g <- c(30, weight_g) # add to the beginning of the vector
weight_g
~~~
{: .language-r}


In the first line, we take the original vector `weight_g`, add the value `90` to the end of it, and save the result back into `weight_g`. Then we add the value `30` to the beginning, again saving the result back into `weight_g`.

> ## Exercise 
>
> What will happen in this example? (hint: use `class()` to check the data type of your objects and type in their names to see what happens):
>
> ~~~
> num_char <- c(1, 2, 3, "a")
> ~~~
> {: .language-r}
{: .challenge}




> ## Solution
> Vectors can be of only one data type. In R, we call converting objects from one class into another class *coercion*. These conversions happen according to a hierarchy, whereby some types get preferentially coerced into other types.
> logical → numeric → character ← logical
{: .solution}

If you were to try to create the following vector:

<a href="{{ page.root }}/fig/vector3.png" >
  <img src="{{ page.root }}/fig/vector3.png" alt="vector3"  width="400" />
</a>


R will coerce it into:

<a href="{{ page.root }}/fig/vector4.png" >
  <img src="{{ page.root }}/fig/vector4.png" alt="vector4"  width="400" />
</a>


## Subsetting vectors

If we want to extract one or several values from a vector, we must provide one or several indices in square brackets. For instance:

~~~
molecules <- c("dna", "rna", "peptide", "protein")
molecules[2]
molecules[c(3, 2)]
~~~
{: .language-r}


We can also repeat the indices to create an object with more elements than the original one:


~~~
more_molecules <- molecules[c(1, 2, 3, 2, 1, 4)]
more_molecules
~~~
{: .language-r}


Finally, it is also possible to get all the elements of a vector except some specified elements using negative indices:

~~~
molecules ## all molecules
molecules[-1] ## all but the first one
molecules[-c(1, 3)] ## all but 1st/3rd ones
molecules[c(-1, -3)] ## all but 1st/3rd ones
~~~
{: .language-r}



#### Tips on variable names
Variables can be given almost any name, such as `x`, `current_temperature`, or `subject_id`. However, there are some rules / suggestions you should keep in mind:

- Make your names explicit and not too long.
- Avoid names starting with a number (`2x` is not valid but `x2` is)
- Avoid names of fundamental functions in R (e.g., `if`, `else`, `for`, see [here](https://statisticsglobe.com/r-functions-list/) for a complete list). 
- Avoid dots (`.`) within a variable name as in `my.dataset`. There are many functions
in R with dots in their names for historical reasons, but because dots have a
special meaning in R (for methods) and other programming languages, it's best to
avoid them. 
- Use nouns for object names and verbs for function names
- Keep in mind that **R is case sensitive** (e.g., `genome_length` is different from `Genome_length`)
- Be consistent with the styling of your code (where you put spaces, how you name variable, etc.). In R, two popular style guides are [Hadley Wickham's style guide](http://adv-r.had.co.nz/Style.html) and [Google's](http://web.stanford.edu/class/cs109l/unrestricted/resources/google-style.html).

***
#### Best practices

Before we move on to more complex concepts and getting familiar with the language, we want to point out a few things about best practices when working with R which will help you stay organized in the long run:

* Code and workflow are more reproducible if you can document everything that we do. Your end goal is not just to "do stuff", but to do it in a way that anyone can easily and exactly replicate your workflow and results. **All code should be written in the script editor and saved to file, rather than working in the console.** 
* The **R console** should be mainly used to inspect objects, test a function or get help. 
* Use `#` signs to comment. **Comment liberally** in your R scripts. This will help future you and other collaborators know what each line of code (or code block) was meant to do. Anything to the right of a `#` is ignored by R. 



### Factors

A **factor** is a special type of vector that is used to **store categorical data**. Each unique category is referred to as a **factor level** (i.e. category = level). Factors are built on top of integer vectors such that each **factor level** is assigned an **integer value**, creating value-label pairs. 

For instance, if we have four animals and the first animal is female, the second and third are male, and the fourth is female, we could create a factor that appears like a vector, but has integer values stored under-the-hood. The integer value assigned is a one for females and a two for males. The numbers are assigned in alphabetical order, so because the f- in females comes before the m- in males in the alphabet, females get assigned a one and males a two. In later lessons we will show you how you could change these assignments.

<a href="{{ page.root }}/fig/factors_sm.png" >
  <img src="{{ page.root }}/fig/factors_sm.png" alt="factors_sm"  width="400" />
</a>


Let's create a factor vector and explore a bit more.  We'll start by creating a character vector describing three different levels of expression. Perhaps the first value represents expression in mouse1, the second value represents expression in mouse2, and so on and so forth:

~~~
# Create a character vector and store the vector as a variable called 'expression'
expression <- c("low", "high", "medium", "high", "low", "medium", "high")
~~~
{: .language-r}


Now we can convert this character vector into a *factor* using the `factor()` function:

~~~
# Turn 'expression' vector into a factor
expression <- factor(expression)
~~~
{: .language-r}


So, what exactly happened when we applied the `factor()` function? 

<a href="{{ page.root }}/fig/factors_new.png" >
  <img src="{{ page.root }}/fig/factors_new.png" alt="factors_new"  width="400" />
</a>


The expression vector is categorical, in that all the values in the vector belong to a set of categories; in this case, the categories are `low`, `medium`, and `high`. By turning the expression vector into a factor, the **categories are assigned integers alphabetically**, with high=1, low=2, medium=3. This in effect assigns the different factor levels. You can view the newly created factor variable and the levels in the **Environment** window.

<a href="{{ page.root }}/fig/factors.png" >
  <img src="{{ page.root }}/fig/factors.png" alt="factors"  width="400" />
</a>


> **Exercise**
> 
> Let's say that in our experimental analyses, we are working with three different sets of cells: normal, cells knocked out for geneA (a very exciting gene), and cells overexpressing geneA. We have three replicates for each celltype.
> 
> 1. Create a vector named `samplegroup` with nine elements: 3 control ("CTL") values, 3 knock-out ("KO") values, and 3 over-expressing ("OE") values.
> 
> 2. Turn `samplegroup` into a factor data structure.
{: .challenge} 



## Matrix

A `matrix` in R is a collection of vectors of **same length and identical datatype**. Vectors can be combined as columns in the matrix or by row, to create a 2-dimensional structure.

<a href="{{ page.root }}/fig/matrix.png" >
  <img src="{{ page.root }}/fig/matrix.png" alt="factors"  width="400" />
</a>

Matrices are used commonly as part of the mathematical machinery of statistics. They are usually of numeric datatype and used in computational algorithms to serve as a checkpoint. For example, if input data is not of identical data type (numeric, character, etc.), the `matrix()` function will throw an error and stop any downstream code execution.



