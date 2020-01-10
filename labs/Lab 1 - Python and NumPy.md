---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
**PUT YOUR FULL NAME(S) HERE**


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


Nothing is unclear or needs further explanation.


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
```

```python
a = np.full((6,4), fill_value=2)
```

## Exercise 2

```python
b = np.eye(N=6,M=4)*2 + np.full((6, 4), fill_value=1)
```

## Exercise 3

```python
# Element-wise multiplication works
c = a * b

# Dot product cannot be run because the shapes do not work
# d = np.dot(a, b)
```

Element-wise multiplication of numpy arrays using * works because the two arrays have the same shape. The arrays cannot be matrix multiplied using dot() because the number of rows in **a** does not match the number of columns in **b**.


## Exercise 4

```python
np.dot(a.transpose(), b)

np.dot(a, b.transpose())
```

The result of np.dot(**a**, **b**) will have **a**'s number of rows and **b**'s number of columns.


## Exercise 5

```python
def print_stuff():
    print("Stuff")

print_stuff()
```

## Exercise 6

```python
def summarize_random_arrays():
    a = np.random.rand(3, 4)
    b = np.random.rand(3, 4)
    print("a:", a)
    print("b:", b)
    print("a+b:", a+b)
    print("mean of a:", np.mean(a))
    print("mean of b:", np.mean(b))

summarize_random_arrays()
```

## Exercise 7

```python
def num_ones(arr):
    count = 0
    for v in arr.flatten():
        if v == 1.0:
            count += 1
    return count

print(num_ones(np.full((2, 3), fill_value=1.0)))
print(num_ones(np.eye(N=6,M=4)))

print(np.sum(np.where(np.full((2, 3), fill_value=1.0) == 1.0, 1, 0)))
print(np.sum(np.where(np.eye(N=6,M=4) == 1.0, 1, 0)))
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd
```

```python
a = pd.DataFrame(np.full((6, 4), fill_value=2.0))
a
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
b = pd.DataFrame(np.eye(N=6,M=4)*2 + np.full((6, 4), fill_value=1))
b
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
a * b

# matrix multiplication will still fail due to shape disagreement
# I'm also unsure how to perform matrix multiplication on
# dataframes without first converting to ndarrays...
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
def count_ones(df):
    return df[df == 1.0].sum().sum()

count_ones(b)
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
titanic_df.set_index('sex',inplace=True)
titanic_df.loc['female']
```

## Exercise 14
How do you reset the index?

```python
# If you use .reset_index(inplace=True) then the dataframe will
# create a new unnamed index instead of using the "index" column

titanic_df.set_index('index', inplace=True)
titanic_df
```

```python

```
