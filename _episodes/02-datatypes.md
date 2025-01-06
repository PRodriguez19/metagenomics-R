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

We know that variables are like buckets, and so far we have seen that bucket filled with a single value. Even when `number` was created, the result of the mathematical operation was a single value. **Variables can store more than just a single value, they can store a multitude of different data structures.** These include, but are not limited to, vectors (`c`), factors (`factor`), matrices (`matrix`), data frames (`data.frame`) and lists (`list`).


### Vectors

A vector is the most common and basic data structure in R, and is pretty much the workhorse of R. It's basically just a collection of values, mainly either numbers,

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


**Note that all values in a vector must be of the same data type.** If you try to create a vector with more than a single data type, R will try to coerce it into a single data type. 

For example, if you were to try to create the following vector:

<a href="{{ page.root }}/fig/vector3.png" >
  <img src="{{ page.root }}/fig/vector3.png" alt="vector3"  width="400" />
</a>


R will coerce it into:

<a href="{{ page.root }}/fig/vector4.png" >
  <img src="{{ page.root }}/fig/vector4.png" alt="vector4"  width="400" />
</a>


The analogy for a vector is that your bucket now has different compartments; these compartments in a vector are called *elements*. 

Each **element** contains a single value, and there is no limit to how many elements you can have. A vector is assigned to a single variable, because regardless of how many elements it contains, in the end it is still a single entity (bucket). 

Let's create a vector of genome lengths and assign it to a variable called `glengths`. 

Each element of this vector contains a single numeric value, and three values will be combined together into a vector using `c()` (the combine function). All of the values are put within the parentheses and separated with a comma.

~~~
# Create a numeric vector and store the vector as a variable called 'glengths'
glengths <- c(4.6, 3000, 50000)
glengths
~~~
{: .language-r}


*Note your environment shows the `glengths` variable is numeric (num) and tells you the `glengths` vector starts at element 1 and ends at element 3 (i.e. your vector contains 3 values) as denoted by the [1:3].*


A vector can also contain characters. Create another vector called `species` with three elements, where each element corresponds with the genome sizes vector (in Mb).

~~~
# Create a character vector and store the vector as a variable called 'species'
species <- c("ecoli", "human", "corn")
species
~~~
{: .language-r}

What do you think would happen if we forgot to put quotations around one of the values? Let's test it out with corn.

~~~
# Forget to put quotes around corn
species <- c("ecoli", "human", corn)
~~~
{: .language-r}


Note that RStudio is quite helpful in color-coding the various data types. We can see that our numeric values are blue, the character values are green, and if we forget to surround corn with quotes, it's black. What does this mean? Let's try to run this code.

When we try to run this code we get an error specifying that object 'corn' is not found. What this means is that R is looking for an object or variable in my Environment called 'corn', and when it doesn't find it, it returns an error. If we had a character vector called 'corn' in our Environment, then it would combine the contents of the 'corn' vector with the values "ecoli" and "human".

Since we only want to add the value "corn" to our vector, we need to re-run the code with the quotation marks surrounding corn. A quick way to add quotes to both ends of a word in RStudio is to highlight the word, then press the quote key.

~~~
# Create a character vector and store the vector as a variable called 'species'
species <- c("ecoli", "human", "corn")
~~~
{: .language-r}


> ## Exercise 
>
> Create a vector of numeric and character values by _combining_ the two vectors that we just created (`glengths` and `species`). Assign this combined vector to a new variable called `combined`. *Hint: you will need to use the combine `c()` function to do this*. 
> Print the `combined` vector in the console, what looks different compared to the original vectors?
{: .challenge} 



#### Tips on variable names
Variables can be given almost any name, such as `x`, `current_temperature`, or
`subject_id`. However, there are some rules / suggestions you should keep in mind:

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



