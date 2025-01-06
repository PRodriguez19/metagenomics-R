---
title: "Data Frame Manipulation"
teaching: 10
exercises: 10
questions:
- "Data-frames. What are they, and how to manage them? "
objectives:
- "Understand what is a data-frame and learn to manipulate it."
keypoints:
- "Data-frames contain multiple columns with different types of data."
---
## Data-frames

A `data.frame` is similar to a matrix in that it's a collection of vectors of the **same length** and each vector represents a column. However, in a dataframe **each vector can be of a different data type** (e.g., characters, integers, factors). In the data frame pictured below, the first column is character, the second column is numeric, the third is character, and the fourth is logical.

<a href="{{ page.root }}/fig/dataframe.png" >
  <img src="{{ page.root }}/fig/dataframe.png" alt="dataframe" />
</a>


A data frame is the most common way of storing data in R, and if used systematically makes data analysis easier. 

We can create a dataframe by bringing **vectors** together to **form the columns**. We do this using the `data.frame()` function, and giving the function the different vectors we would like to bind together. *This function will only work for vectors of the same length.*

~~~
# Create a data frame and store it as a variable called 'df'
df <- data.frame(species, glengths)
~~~
{: .language-r}


We can see that a new variable called `df` has been created in our `Environment` within a new section called `Data`. In the `Environment`, it specifies that `df` has 3 observations of 2 variables. What does that mean? In R, rows always come first, so it means that `df` has 3 rows and 2 columns. We can get additional information if we click on the blue circle with the white triangle in the middle next to `df`. It will display information about each of the columns in the data frame, giving information about what the data type is of each of the columns and the first few values of those columns.

Another handy feature in RStudio is that if we hover the cursor over the variable name in the `Environment`, `df`, it will turn into a pointing finger. If you click on `df`, it will open the data frame as it's own tab next to the script editor. We can explore the table interactively within this window. To close, just click on the X on the tab.

As with any variable, we can print the values stored inside to the console if we type the variable's name and run. 

~~~
df
~~~
{: .language-r}

#### Data frame example 

We can create a more complex data frame using the following syntax:

~~~
df <- data.frame(id = c("a", "b", "c"),
                 x = c(1, 2, 3),
                 y = c(TRUE, TRUE, FALSE))
~~~
{: .language-r}


> **Exercise**
> 
> Create a data frame called `tax_table` with the following vectors as columns:
> 
>   + id: Family, Genus, Species
>   + sample1: Rhodo, Rhodobacter, capsulatus
>   + sample2: Rhodo, Paracoccus, yeei 
{: .challenge} 


  
You have just created your first data frame. A data-frame is a collection of vectors (i.e. a list) whose components must be of the same data type within each vector. To view the data frame use the following: 


~~~
View(tax_table)
~~~
{: .language-r}

We can pull out columns from the new object using the `$` operator. In order to use it, you will need to write the name of your data frame followed by the `$` operator with the name of the column you want to extract.

~~~
tax_table$Species
~~~
{: .language-r}




