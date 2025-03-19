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







